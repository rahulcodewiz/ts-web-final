---
layout: post
title: MCP Request End to End Request Tracing
date: 2025-03-01 00:00:02.000000000 -08:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Python
- MCP
tags:
- python
- agent
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/mcp-e2e-request-tracing/"
---

When debugging distributed systems, you need to track requests across multiple services and async operations. This article shows how to implement automatic request tracing using Python's `contextvars` module, ensuring every log entry includes session and request identifiers for easy correlation.

## The Request Tracing System

This implementation provides production-ready request tracing with several key features:

1. **Automatic Context Propagation**: Using `contextvars` to propagate trace IDs across async boundaries
2. **Flexible ID Extraction**: Supporting multiple sources for session IDs (headers, query params, auth tokens)

## Core Architecture: Context Variables

Python's `contextvars` module lets you propagate context across async operations without manual parameter passing. Set it once, use it everywhere.

```python
# Context variables for request tracing
session_id_ctx = contextvars.ContextVar("session_id", default=None)
request_id_ctx = contextvars.ContextVar("request_id", default=None)

@dataclass
class RequestMetadata:
    session_id: Optional[str] = None
    request_id: Optional[str] = None
    start_time: float = field(default_factory=time.time)
    method: Optional[str] = None
    path: Optional[str] = None
    transport_type: Optional[str] = None
```

Once you set these context variables, they will appear in every async operation within that request. No manual passing required.

## ASGI Middleware Implementation

The middleware captures or creates IDs when requests arrive and sets up the tracing context:

```python
class RequestTracingMiddleware(BaseHTTPMiddleware):
    async def dispatch(self, request: Request, call_next) -> Response:
        # Extract or generate IDs
        session_id = self._extract_session_id(request)
        request_id = generate_request_id()
        
        # Create and set metadata
        metadata = RequestMetadata(
            session_id=session_id,
            request_id=request_id,
            method=request.method,
            path=str(request.url.path)
        )
        set_request_metadata(metadata)
        
        # Process request with context
        response = await call_next(request)
        
        # Add tracing headers to response
        response.headers["X-Request-ID"] = request_id
        return response
```

## Flexible Session ID Extraction

The system intelligently checks multiple sources for session IDs:

- X-Session-ID header
- X-Correlation-ID header  
- session_id query parameter
- Authorization Bearer token (for SSE connections)
- Generates new ID if none found

This flexibility means clients can provide session IDs in whatever way works best for their architecture.

## Enhanced Logging

Every log entry automatically includes trace IDs through a custom logging filter:

```python
class RequestTracingFilter(logging.Filter):
    def filter(self, record):
        # Get current context values
        session_id = get_session_id()
        request_id = get_request_id()
        
        # Add to log record
        record.session_id = session_id[:8] if session_id else "none"
        record.request_id = request_id if request_id else "none"
        return True
```

Your logs now look like this:

```bash
2024-01-15 10:30:15 - INFO - [req=a1b2c3d4|session=12345678] - Processing payment for user Alice
2024-01-15 10:30:16 - ERROR - [req=a1b2c3d4|session=12345678] - Payment gateway timeout
```

Need to debug a user's issue? Just grep for their session ID. Want to trace a specific request? Search for the request ID.

## Seamless Async Support

The beautiful part? When you spawn async tasks, they inherit the same context:

```python
async def handle_parallel_tasks(task_count: int):
    logger.info(f"Starting {task_count} parallel tasks")
    
    # All these tasks will have the same session/request IDs!
    tasks = [
        asyncio.create_task(worker_task(i)) 
        for i in range(task_count)
    ]
    
    results = await asyncio.gather(*tasks)
    logger.info("All tasks completed")
```

Every log from those parallel workers will have the same trace IDs. No more guessing which task belongs to which request.

## Integration

Just add the middleware to your Starlette/FastAPI application:

```python
app = Starlette(
    routes=[...],
    middleware=[
        Middleware(RequestTracingMiddleware),
    ]
)
```

That's it. Your entire application now has automatic request tracing.

![MCP Request Tracing]({{ site.baseurl }}/assets/images/mcp_tracing.png)

## Impact

After implementing this the debugging time can be reduced significantly and complex async flows are now completely traceable

---

**Full Implementation**: Check out the complete working code at [mcp-experiments](https://github.com/rahulcodewiz/mcp-experiments.git).