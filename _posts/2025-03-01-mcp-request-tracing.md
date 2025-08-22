<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MCP Request Tracing</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            min-height: 100vh;
        }
        
        .container {
            background: white;
            border-radius: 12px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            padding: 25px;
            max-width: 900px;
            width: 100%;
        }
        
        h1 {
            text-align: center;
            color: #333;
            margin-bottom: 5px;
            font-size: 20px;
        }
        
        .subtitle {
            text-align: center;
            color: #666;
            margin-bottom: 20px;
            font-size: 12px;
        }
        
        .visualization {
            display: flex;
            gap: 25px;
            margin-bottom: 20px;
        }
        
        .column {
            flex: 1;
        }
        
        .column-title {
            font-weight: bold;
            color: #444;
            margin-bottom: 12px;
            padding: 6px;
            background: #f0f0f0;
            border-radius: 6px;
            text-align: center;
            font-size: 13px;
        }
        
        .request-box {
            background: #fff;
            border: 2px solid #ddd;
            border-radius: 8px;
            padding: 10px;
            margin-bottom: 10px;
            position: relative;
            font-size: 12px;
        }
        
        .user-label {
            font-weight: bold;
            color: #667eea;
            margin-bottom: 5px;
            font-size: 12px;
        }
        
        .request-details {
            font-size: 11px;
            color: #666;
            line-height: 1.4;
        }
        
        .request-details div {
            margin-bottom: 2px;
        }
        
        .timestamp {
            color: #999;
            font-size: 10px;
        }
        
        .log-entry {
            background: #1a1a1a;
            color: #00ff00;
            font-family: 'Courier New', monospace;
            font-size: 10px;
            padding: 8px;
            margin-bottom: 6px;
            border-radius: 4px;
            line-height: 1.3;
            white-space: nowrap;
            overflow-x: auto;
        }
        
        .log-entry::-webkit-scrollbar {
            height: 3px;
        }
        
        .log-entry::-webkit-scrollbar-track {
            background: #333;
        }
        
        .log-entry::-webkit-scrollbar-thumb {
            background: #666;
            border-radius: 2px;
        }
        
        .log-timestamp {
            color: #888;
        }
        
        .log-level-info {
            color: #00ff00;
        }
        
        .log-level-warn {
            color: #ffaa00;
        }
        
        .trace-ids {
            color: #00ffff;
            font-weight: bold;
        }
        
        .arrow {
            position: absolute;
            right: -20px;
            top: 50%;
            transform: translateY(-50%);
            color: #667eea;
            font-size: 16px;
        }
        
        .legend {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 15px;
            padding-top: 15px;
            border-top: 1px solid #eee;
            font-size: 11px;
        }
        
        .legend-item {
            display: flex;
            align-items: center;
            gap: 6px;
            color: #666;
        }
        
        .legend-color {
            width: 14px;
            height: 14px;
            border-radius: 3px;
        }
        
        .session-alice { background: #667eea; }
        .session-bob { background: #f093fb; }
        
        .highlight-alice {
            border-left: 3px solid #667eea !important;
        }
        
        .highlight-bob {
            border-left: 3px solid #f093fb !important;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Request Tracing Visualization</h1>
        <p class="subtitle">How session & request IDs connect mixed logs</p>
        
        <div class="visualization">
            <div class="column">
                <div class="column-title">🌐 User Requests</div>
                
                <div class="request-box highlight-alice">
                    <div class="user-label">Alice - Payment</div>
                    <div class="request-details">
                        <div>POST /api/payment</div>
                        <div>Session: <strong>abc12345</strong></div>
                        <div>Request: <strong>req-001</strong></div>
                        <div class="timestamp">10:30:15</div>
                    </div>
                    <div class="arrow">→</div>
                </div>
                
                <div class="request-box highlight-bob">
                    <div class="user-label">Bob - Profile</div>
                    <div class="request-details">
                        <div>GET /api/profile</div>
                        <div>Session: <strong>def67890</strong></div>
                        <div>Request: <strong>req-002</strong></div>
                        <div class="timestamp">10:30:15</div>
                    </div>
                    <div class="arrow">→</div>
                </div>
                
                <div class="request-box highlight-alice">
                    <div class="user-label">Alice - Status</div>
                    <div class="request-details">
                        <div>GET /api/status</div>
                        <div>Session: <strong>abc12345</strong></div>
                        <div>Request: <strong>req-003</strong></div>
                        <div class="timestamp">10:30:16</div>
                    </div>
                    <div class="arrow">→</div>
                </div>
            </div>
            
            <div class="column">
                <div class="column-title">📝 Mixed Application Logs</div>
                
                <div class="log-entry">
                    <span class="log-timestamp">10:30:15</span> - <span class="log-level-info">INFO</span> - <span class="trace-ids">[req=req-001|session=abc12345]</span> - Processing payment
                </div>
                
                <div class="log-entry">
                    <span class="log-timestamp">10:30:15</span> - <span class="log-level-info">INFO</span> - <span class="trace-ids">[req=req-002|session=def67890]</span> - Loading profile
                </div>
                
                <div class="log-entry">
                    <span class="log-timestamp">10:30:15</span> - <span class="log-level-info">INFO</span> - <span class="trace-ids">[req=req-001|session=abc12345]</span> - Validating payment
                </div>
                
                <div class="log-entry">
                    <span class="log-timestamp">10:30:15</span> - <span class="log-level-info">INFO</span> - <span class="trace-ids">[req=req-002|session=def67890]</span> - Profile retrieved
                </div>
                
                <div class="log-entry">
                    <span class="log-timestamp">10:30:16</span> - <span class="log-level-warn">WARN</span> - <span class="trace-ids">[req=req-001|session=abc12345]</span> - Gateway slow
                </div>
                
                <div class="log-entry">
                    <span class="log-timestamp">10:30:16</span> - <span class="log-level-info">INFO</span> - <span class="trace-ids">[req=req-001|session=abc12345]</span> - Payment complete
                </div>
                
                <div class="log-entry">
                    <span class="log-timestamp">10:30:16</span> - <span class="log-level-info">INFO</span> - <span class="trace-ids">[req=req-003|session=abc12345]</span> - Status check
                </div>
            </div>
        </div>
        
        <div class="legend">
            <div class="legend-item">
                <div class="legend-color session-alice"></div>
                <span>Alice (abc12345)</span>
            </div>
            <div class="legend-item">
                <div class="legend-color session-bob"></div>
                <span>Bob (def67890)</span>
            </div>
        </div>
    </div>
</body>
</html>

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

## Impact

After implementing this the debugging time can be reduced significantly and complex async flows are now completely traceable

---

**Full Implementation**: Check out the complete working code at [mcp-experiments](https://github.com/rahulcodewiz/mcp-experiments.git).