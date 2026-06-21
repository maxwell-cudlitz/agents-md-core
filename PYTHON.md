---
name: python-conventions
description: Python coding conventions and standards. Use when writing or reviewing Python code.
---

Run python code within virtual environments maintained at the root of the project named venv/. 

> python3 -m venv venv
> source venv/bin/activate

Always gitignore venv/ and pycache directories

Dependencies should be pinned to explicit version and frozen to requirements.txt

Let exceptions propagate naturally. Do not catch exceptions unless you can handle them meaningfully. At service/module boundaries, wrap with context using raise X from err. Log at the outermost layer only.
