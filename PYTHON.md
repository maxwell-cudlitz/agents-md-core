---
name: python-conventions
description: Python coding conventions and standards. Use when writing or reviewing Python code.
---

Run python code within virtual environments maintained at the root of the project named venv/. 

> python3 -m venv venv
> source venv/bin/activate

Always gitignore venv/ and pycache directories

Dependencies should be pinned to explicit version and frozen to requirements.txt

## Config

Use `dynaconf` for configuration loading. It provides layered YAML config with environment variable overrides using the `__` nesting delimiter out of the box. Initialize with `Dynaconf(settings_files=["config.yaml", "config.local.yaml"], envvar_prefix="APP")`.

## Error Handling

Let exceptions propagate naturally. Do not catch exceptions unless you can handle them meaningfully. At service/module boundaries, wrap with context using raise X from err. Log at the outermost layer only.
