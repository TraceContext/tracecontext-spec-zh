# TraceContext Specs
Specification for TraceContext propagation format.

Trace 上下文传输规范。

译者：[吴晟](https://github.com/wu-sheng)

## Goal
这份规范定义trace上下文信息，跨系统传输时的规范。我们的目标通过和社区共建这份协议，通过这份协议，
大量的追踪和诊断产品之间，可以相互交互。

## HTTP Format
HTTP格式定义 [查看](HTTP_HEADER_FORMAT.md)

## Binary Format
TODO: add link here

## Reference Implementations
TODO: add link here

## Why are we doing this?
* If this becomes popular, frameworks and other services will automatically pass trace IDs through for correlated requests. This would prevent traces from hitting dead ends when a request reaches an un-instrumented service.
* Once aligned on a header name, we can ask for a CORS exception from the W3C. This would allow browsers to attach trace IDs to requests and submit tracing data to a distributed tracing service.
* Loggers can reliably parse trace / span IDs and include them in logs for correlation purposes.
* Customers can use multiple tracing solutions (Zipkin + New Relic) at the same time and not have to worry about propagating two sets of context headers.
* Frameworks can *bless* access to the trace context even if they prevent access to underlying request headers, making it available by default.
