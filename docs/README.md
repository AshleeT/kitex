# CloudWeGo-Kitex
Kitex [kaɪt'eks] is a Golang-based, scalable and performant RPC framework that can help developers build microservices. As more and more organizations are now choosing Golang, if you have requirements for microservice performance and want to do some customization, Kitex will be a good choice.

## Basic Features

- **High performance**

Kitex supports [Netpoll](https://github.com/cloudwego/netpoll), a self-developed high-performance network library, which has significant performance advantages over go net.

- **Scalability**

Kitex provides more extension interfaces and default extension implementations. Developers can also customize extensions according to their own needs (please refer to the framework extension section below).

- **Multi-message protocol**

Kitex is designed to be extensible to support multiple RPC messaging protocols. The initial release contains support for **Thrift**, **Kitex Protobuf** and **gRPC**, in which Kitex Protobuf is a Kitex custom Protobuf messaging protocol with a protocol format similar to Thrift. Kitex also supports developers extending their own messaging protocols.

- **Multi-transport protocol**

For service governance, Kitex supports **TTHeader** and **HTTP2**. TTHeader can be used in conjunction with Thrift and Kitex Protobuf; HTTP2 is currently mainly used with the gRPC protocol, and it will support Thrift in the future.

- *Multi-interaction*

Kitex supports **PingPong**, **one-way**, and **two-way Streaming**. Among them, One-way currently only supports Thrift protocol, two-way Streaming only supports gRPC, and Kitex will support Thrift's two-way Streaming in the future.

- **Service Governance**

Kitex integrates service governance modules such as service registry, service discovery, load balancing, fusing, current limiting, retry, monitoring, link tracking, logging, diagnostics, etc. Most of these have been provided with default extensions, and users can choose to integrate.

- **Code generation**

Kitex has built-in code generation tools that support generating **Thrift**, **Protobuf**, and scaffold code.

## Performance

We compared the performance of Kitex with some popular RPC frameworks ([test code](https://github.com/cloudwego/kitex-benchmark)), such as [gRPC](https://github.com/grpc/grpc) and [RPCX](https://github.com/smallnest/rpcx), both using Protobuf protocol. The test results show that [Kitex](https://github.com/cloudwego/kitex) performs better.

*Note: The performance benchmarks obtained from the experiment are for reference only, because there are many factors that can affect the actual performance in application scenarios.*

### Test environment

- CPU: Intel(R) Xeon(R) Gold 5118 CPU @ 2.30GHz, 4 cores
- Memory: 8GB
- OS: Debian 5.4.56.bsk.1-amd64 x86_64 GNU/Linux
- Go: 1.15.4

### Concurrency performance 

Echo 1KB, change the amount of concurrency.

QPS|TP99|TP999
----|----|----
![](https://github.com/cloudwego/kitex/blob/develop/docs/images/performance_concurrent_qps.png)|![](https://github.com/cloudwego/kitex/blob/develop/docs/images/performance_concurrent_tp99.png)|![](https://github.com/cloudwego/kitex/blob/develop/docs/images/performance_concurrent_tp999.png)

### Throughput performance

Concurrent 100, change packet size.

QPS|TP99|TP999
----|----|----
![](https://github.com/cloudwego/kitex/blob/develop/docs/images/performance_bodysize_qps.png)|![](https://github.com/cloudwego/kitex/blob/develop/docs/images/performance_bodysize_tp99.png)|![](https://github.com/cloudwego/kitex/blob/develop/docs/images/performance_bodysize_tp999.png)

## Documentation

- [**Getting Started**](https://github.com/cloudwego/kitex/blob/develop/docs/guide/getting_started.md)
- **User Guide**
  - Basic Features
    - [Message Type](https://github.com/cloudwego/kitex/blob/develop/docs/guide/basic-features/message_type.md)
    - Protocols
    - Transport Protocol TTheader
    - Direct Access
    - Connection Pool
    - [Timeout Control](https://github.com/cloudwego/kitex/blob/develop/docs/guide/basic-features/timeout.md)
    - [Request Retry](https://github.com/cloudwego/kitex/blob/develop/docs/guide/basic-features/retry.md)
    - [LoadBalancer](https://github.com/cloudwego/kitex/blob/develop/docs/guide/basic-features/loadbalance.md)
    - [Circuit Breaker](https://github.com/cloudwego/kitex/blob/develop/docs/guide/basic-features/circuitbreaker.md)
    - [Rate Limiting](https://github.com/cloudwego/kitex/blob/develop/docs/guide/basic-features/limiting.md)
    - [Tracing stats level control](https://github.com/cloudwego/kitex/blob/develop/docs/guide/basic-features/tracing.md)
    - [Logging](https://github.com/cloudwego/kitex/blob/develop/docs/guide/basic-features/logging.md)
    - [HttpResolver](https://github.com/cloudwego/kitex/blob/develop/docs/guide/basic-features/HTTP_resolver.md)
  - Governance Features
    - Service Discovery
    - Monitoring
    - Link Tracking
    - Custom Access Control
  - Advanced Features
    - Generic Reference
    - [Server SDK Mode](https://github.com/cloudwego/kitex/blob/develop/docs/guide/basic-features/invoker.md)
  - Code Generation
    - [Tools](https://github.com/cloudwego/kitex/blob/develop/docs/guide/basic-features/code_generation.md)
    - [Combined Service](https://github.com/cloudwego/kitex/blob/develop/docs/guide/basic-features/combine_service.md)
  - Framework Extension
    - [Middleware Extensions](https://github.com/cloudwego/kitex/blob/develop/docs/guide/extension/middleware.md)
    - [Suite Extensions](https://github.com/cloudwego/kitex/blob/develop/docs/guide/extension/suite.md)
    - Service Registry
    - Service Discovery
    - [Customize LoadBalancer](https://github.com/cloudwego/kitex/blob/develop/docs/guide/extension/loadbalance.md)
    - Monitoring
    - [Logging](https://github.com/cloudwego/kitex/blob/develop/docs/guide/basic-features/logging.md)
    - Codec
    - Transport Module
    - Transport Pipeline
    - Meta-information Transport
    - Diagnostic Module
- **Reference**
	- [Exception Instruction](https://github.com/cloudwego/kitex/blob/develop/docs/reference/exception.md)
	- Version History
- **FAQ**

## Related Projects

- [Netpoll](https://github.com/cloudwego/netpoll): A high-performance network library.
- [kitex-contrib](https://github.com/kitex-contrib): A partial extension library of Kitex, which users can integrate into Kitex through options according to their needs.
- [Example](https://github.com/cloudwego/kitex/blob/develop/TODO): Use examples of Kitex.

## Blogs

- [Performance Optimization Practice of Go RPC framework Kitex](https://mp.weixin.qq.com/s/Xoaoiotl7ZQoG2iXo9_DWg)
- [Practice of ByteDance on Go Network Library](https://mp.weixin.qq.com/s?__biz=MzI1MzYzMjE0MQ==&mid=2247485756&idx=1&sn=4d2712e4bfb9be27a790fa15159a7be1&chksm=e9d0c2dedea74bc8179af39888a5b2b99266587cad32744ad11092b91ec2e2babc74e69090e6&scene=21#wechat_redirect)

## Contributing

[Contributing](https://github.com/cloudwego/kitex/blob/develop/CONTRIBUTING.md)

## License

Kitex is distributed under the [Apache License, version 2.0](https://github.com/cloudwego/kitex/blob/develop/LICENSE). The licenses of third parity dependencies of Kitex are explained [here](https://github.com/cloudwego/kitex/blob/develop/licenses).

## Community
- Email: [conduct@cloudwego.io](conduct@cloudwego.io)
- Issues: [Issues](https://github.com/cloudwego/kitex/issues)
- Lark: Scan the QR code below with [Lark](https://www.larksuite.com/zh_cn/download) to join our CloudWeGo/kitex user group.

![](https://github.com/cloudwego/kitex/blob/develop/docs/images/LarkGroup.jpg)
