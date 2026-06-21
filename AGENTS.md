## Documentation

When generating code, keep and maintain two document files; AGENTS.md and README.md in the root of the repo. An AGENTS file should lay out the structure of the repository and all functionality so that agentic models can maintain the work inside the repo. A README.md should describe functionality for users at the top of the file, and give key insights for developers.

When generating code, maintain both inline and block comments. Inline comments where necessary, and block comments public functions and non-obvious internal functions, and at the top of every file.

## Logging

Write structured logs (JSON lines) to stderr. Never write to files or manage rotation — let the deployment environment handle log routing.

- **Stdout** is for program output/data only.
- **Stderr** is for all diagnostic/log messages.
- Control verbosity via `LOG_LEVEL` env var (debug, info, warn, error).
- Support `LOG_FORMAT=text` for human-readable output during local development.
- Include timestamp, level, message, and relevant context fields in each log line.

## Design

When designing a new feature, first reflect and ask if a generic version would be appropriate; For example, if designing a feature that ingests some data of a certain type, if that data being ingested may be generified, ask if this should be implemented as an interface.

Apps should be written as config-driven unix style applications. 

Keep in mind CNCF standards when designing for distributed systems.
1.) Distributable, such that applications are built as loosely coupled services, each of which performs a single function. This supports horizontal scalability.
2.) Observable, such that requests crossing multiple services can be tracked through built-in monitoring, tracing and logging features to improve system understanding and reliability.
3.) Portable, such that applications can take full advantage of cloud computing by not being tied to specific vendors or implementations.
4.) Interoperable, such that services expose their functionality through APIs, allowing easy integration throughout the system.
5.) Available, such that failure in a service is handled gracefully with minimal disruption to the application as a whole.

If writing for distributed systems, maintain the unix-style application and wrap it with a REST api.

For standalone CLI tools and scripts, prioritize simplicity

## Coding style

When writing to a file, if the filesize exceeds 250 lines, review and see if the file may be broken into either smaller processes, optimized into fewer lines, or otherwise simplified. Prefer simple, easily-read and audited code to complex patterns at all times. Code should be DRY at all times.