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
* 如果这份规范被大家接受，框架和其他服务帮助传递这些ID，这样可以避免当一个请求经过一个没有被追踪的服务时，调用链断裂。
* 一旦我们在header名称上达成一致，我们可以向W3C请求，将这些名称加入到CORS（跨域资源共享，Cross-Origin Resource Sharing）允许的header名称中。这样允许浏览器将追踪到的请求信息，发送到一个分布式追踪服务上。
* 日志系统确定请求中的trace和span id,并将它们加入到日志中，用于后续关联分析。
* 用户可以同时使用多个追踪系统 (如 Zipkin + New Relic)，而不用担心需要传输两种类型的上下文头信息。
* 某些框架默认会禁止访问请求头信息，利用这份协议，框架可以默认放行这些请求头。

