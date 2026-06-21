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

Apps should be written as config-driven unix style applications. There should be a root-level yaml file that covers base behavior that is loaded into a dict by a config loader. Then, if a local config yaml is provided, it will override matching values. Finally, environment variables (KEY_ROOT__KEY_CHILD -> KEY_ROOT.KEY_CHILD) will override those

For standalone CLI tools and scripts, prioritize simplicity. Unit tests should be written for branching functions.

Do not swallow errors silently. Propagate errors using the language's idiomatic mechanism. Only handle an error at the layer that can meaningfully respond to it. At module or serviceboundaries, wrap errors with context describing what operation failed. Log errors once, at the outermost handler.

## Coding style

When writing to a file, if the filesize exceeds 250 lines, review and see if the file may be broken into either smaller processes, optimized into fewer lines, or otherwise simplified. Prefer simple, easily-read and audited code to complex patterns at all times. Code should be DRY at all times.