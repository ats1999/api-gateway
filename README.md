<!--
```text
_______
\  ___ `'.                    .          .--.
 ' |--.\  \                 .'|          |__|
 | |    \  '              .'  |          .--.
 | |     |  '     __     <    |          |  |     __
 | |     |  |  .:--.'.    |   | ____     |  |  .:--.'.
 | |     ' .' / |   \ |   |   | \ .'     |  | / |   \ |
 | |___.' /'  `" __ | |   |   |/  .      |  | `" __ | |
/_______.'/    .'.''| |   |    /\  \     |__|  .'.''| |
\_______|/    / /   | |_  |   |  \  \         / /   | |_
              \ \._,\ '/  '    \  \  \        \ \._,\ '/
               `--'  `"  '------'  '---'       `--'  `"
```
-->

<!-- canva logo url -> https://www.canva.com/design/DAGZAdY1d9c/YCHWZRD78H5j0CAWaaF6gw/edit -->

<!-- ![1](https://github.com/user-attachments/assets/9348db35-f589-4dc4-9a03-24924d6d8f2d) --> 

# An API gateway tailored for modern distributed systems

**Dakia** is a high-performance API gateway built with Rust, designed for low-latency request processing. Dakia supports **dynamic configuration updates**, allowing seamless changes to routing rules, authentication settings, rate limits, and other gateway policies **without requiring a restart**. This ensures high availability and adaptability in rapidly evolving microservices architectures. Additional features include request routing, load balancing, caching, and fault tolerance, making it a robust solution for modern distributed systems.

> It's under construction 🦺 🪚 🏗️ 🚧 🔨

## Feature highlights

- **Configurable**: Easily manage API configurations using various formats like YAML, JSON, and HTTP API calls.
- **Extensible**: Add new functionality with support for custom middleware and plugins, written in any programming language (Rust, Java, C++, etc.).
- **Fully Programmable**: Tailor the API Gateway to your specific needs with custom plugins and middleware in multiple languages.
- **Zero Downtime Upgrades**: Perform upgrades and restarts without affecting the availability of your services.
- **Dynamic Middleware**: Add, remove, or modify middleware on the fly without disrupting service.
- **Request and Response Management**: Modify requests before they reach the upstream or read/write responses to meet your application's needs.
- **Real-Time Configuration**: Modify your gateway configuration in real time with no downtime, using HTTP API calls.

Dakia ensures your services stay performant, reliable, and highly customizable, giving you full control.

## Limitations ☠️

> These limitations will be addressed over time as we continue to improve the dakia.

- Currently supports only `UTF-8` character encoding.
- Only the round-robin load balancing algorithm is available at the moment.
- IPv6 addresses are not supported at this time; only IPv4 is supported.
- Currently it supports only `HTTP` protocol

## Reasons to use `Dakia`

- **Security** - Built with Rust, Dakia ensures enhanced memory safety and reduces vulnerabilities compared to services written in C/C++.
- **Performance** - Powered by [pingora](https://github.com/cloudflare/pingora), a battle tested protocol implemention, as it has been serving more than **_40M+_** internet requests per second for more than a few years.
- **Customization** - You need ultimate customization, you can configure, extend and even further program in multiple languages.
- **Asynchronous and Multi-Threaded** – Dakia is designed to handle tasks concurrently, ensuring efficient and high-performance request processing by default.

**_Benchmark of Dakia on a Local Machine (8 CPU Cores, 16GB RAM)_**

```txt
Performance test: 10s @ http://0.0.0.0:80
  - 1 thread, 100 concurrent connections

  Thread Statistics:
    - Average Latency: 699.64µs (±125.23µs)
    - Maximum Latency: 3.77ms
    - Requests per Second: 76.09k (±3.98k)
    - Peak Requests per Second: 81.89k

  Total Requests: 764,590 in 10.10s
  Data Transferred: 80.94MB
  Throughput: 75,678.12 requests/sec
  Transfer Rate: 8.01MB/sec
```

## Architecture

![flow](https://github.com/user-attachments/assets/581b8dd2-c313-4a38-85a1-fd1429104f6a)

## Getting started

- See our [quick starting guide](/docs/quick_start.md)
- See our [docs](/docs/README.md)

<!-- 
## 📊 Progress Tracker

[Dakia Configuration Sample](https://github.com/ats1999/dakia/blob/main/docs/config.sample.yaml)

| Task                                                                                                                                                                   | Status         |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- |
| Configurable(YAML + JSON)                                                                                                                                              | Done ✅        |
| Virtual Host                                                                                                                                                           | Done ✅        |
| Wild card host matching ([Wiki](https://en.wikipedia.org/wiki/Matching_wildcards))                                                                                     | Done ✅        |
| Wild card route ([Wiki](https://en.wikipedia.org/wiki/Matching_wildcards))                                                                                             | Done ✅        |
| Proxy                                                                                                                                                                  | Done ✅        |
| HTTP Protocol Suport                                                                                                                                                   | Done ✅        |
| [Upstream SSL support](https://en.wikipedia.org/wiki/Server_Name_Indication)                                                                                           | Done ✅        |
| Load Balancer                                                                                                                                                          | Done ✅        |
| Filter (MongoDB like query support)                                                                                                                                    | Done ✅        |
| Dakia CLI                                                                                                                                                              | Done ✅        |
| [PCRE](https://www.pcre.org/) support for pattern matching                                                                                                             | Done ✅        |
| Extension, Interceptor & Interceptions Phases (Inbuilt Rust)                                                                                                           | Done ✅        |
| Declarative filter support [(Allows to use MongoDB like query syntax for filtering HTTP requests)](https://github.com/ats1999/dakia/blob/main/docs/config.sample.yaml) | Done ✅        |
| [FFI](https://en.wikipedia.org/wiki/Foreign_function_interface) Support for interceptor                                                                                | Pending        |
| [UDS Support](https://man7.org/linux/man-pages/man7/unix.7.html)                                                                                                       | Pending        |
| Load Balancer Algorithms (Least connection, Least response time, IP/Url hash)                                                                                          | Pending        |
| SSL Support                                                                                                                                                            | Pending        |
| Certbot Integration                                                                                                                                                    | Pending        |
| Controller (API to manage dakia over REST)                                                                                                                             | Done ✅        |
| TCP/UDP Proxy                                                                                                                                                          | Pending        |
| Web Socket Proxy                                                                                                                                                       | Pending        |
| gRPC Proxy                                                                                                                                                             | Pending        |
| Docs                                                                                                                                                                   | In-Progress 🚀 |

### Load Balancing Algorithm

| Algorithm           | Status  |
| ------------------- | ------- |
| Round robin         | Done ✅ |
| Least connection    | Pending |
| Least response time | Pending |
| IP/URL hash         | Pending |

### Interceptor

| Interceptor                                 | Description                                                                                                                                                        | Status  |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------- |
| Server Version                              | Append server version into http response header. E.g `Dakia/1.0.1`                                                                                                 | Done ✅ |
| Request ID                                  | Append request id(UUID) into upstream request and downstream response headers.                                                                                     | Done ✅ |
| Basic Auth                                  | [Basic Authentication](https://en.wikipedia.org/wiki/Basic_access_authentication)                                                                                  | Done ✅ |
| Basic Auth ( External Storage Integration ) | Use external storage for storing user name and password, support hashing.                                                                                          | Pending |
| JWT Auth                                    | [Support JWT authentication](https://jwt.io/)                                                                                                                      | Pending |
| Use File                                    | Read data from a file and return its contents as the response. If the file is not found, respond with a 404 error.                                                 | Done ✅ |
| Use File ( Path rewrite support )           | Allow to rewrite HTTP request path                                                                                                                                 | Pending |
| Try File                                    | Read data from a file and return its contents as the response. If the file is not found, make request to upstream, write response to file and then serve response. | Pending |
| Controller                                  | Allow to update dakia configuration in **_YAML/JSON_** format via REST endpoint without restarting the gateway                                                     | Done ✅ |
| Rate Limiter                                | Token bucket rate limiter algorithm                                                                                                                                | Done ✅ |
| Prometheus Integration                      | Expose server interval metric using prometheus (New TCP connection, Reused TCP connection, TCP connection failure, etc)                                            | Pending |
--> 
