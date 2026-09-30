---
name: wizard
description: Generate a safe, resumable interactive script that guides a human through setup, credential, dashboard, migration, or cutover steps that only a human can perform. Use when the user asks for a guided script or wizard for manual steps. Not for work the agent can safely perform directly.
---

# Wizard

Generate a small interactive script only for setup steps that genuinely require
a human decision, credential, browser action, migration, or cutover. Use the
project's existing scripting conventions and tooling.

## Design the operator journey

Inspect the current configuration and scripts first. For every stage, identify
the source, destination, owner, environment, captured value, sensitivity,
validation, and whether the action is reversible. Show the ordered stages, state
the script path, and confirm both before writing the script.

Make the target and environment unambiguous at every consequential step. Open
or describe the relevant URL before requesting a value. Read secrets without
echoing them and keep them out of arguments, source, output, and logs. Require a
specific confirmation before an irreversible or production action; preserve any
existing four-eyes or separation control.

## Keep the script safe to resume

Make completed stages detectable and reruns idempotent where the underlying
system permits it. Validate inputs before writing them, state exactly where
results are stored, and stop on partial or unexpected state rather than guessing
how to continue.

Validate without executing the wizard: run the language's syntax and lint
checks, such as `bash -n` and `shellcheck` for shell or `python -m py_compile`
for Python, and trace each captured value to its intended destination. Explain
how to run it, what it will mutate, how to recover, and which stages still need
human judgement. Do not generate a wizard for work the agent can safely perform
directly. Never place credentials in source or logs.
