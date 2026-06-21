---
name: cloud-development
description: CNCF standards and distributed systems guidance. Use when designing cloud-native or distributed applications.
---

## Cloud & Distributed Systems

Keep in mind CNCF standards when designing for distributed systems.
1.) Distributable, such that applications are built as loosely coupled services, each of which performs a single function. This supports horizontal scalability.
2.) Observable, such that requests crossing multiple services can be tracked through built-in monitoring, tracing and logging features to improve system understanding and reliability.
3.) Portable, such that applications can take full advantage of cloud computing by not being tied to specific vendors or implementations.
4.) Interoperable, such that services expose their functionality through APIs, allowing easy integration throughout the system.
5.) Available, such that failure in a service is handled gracefully with minimal disruption to the application as a whole.

If writing for distributed systems, maintain the unix-style application and wrap it with a REST api. When writing for distributed systems, code should have both integration and unit tests.
