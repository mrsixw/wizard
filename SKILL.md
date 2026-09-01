---
name: wizard
description: Generate an interactive script for manual setup, credentials, dashboard steps, migrations, or cutovers that only a human can perform.
---

# Wizard

1. Identify every manual stage, captured value, destination, sensitivity, and irreversible action.
2. Show the ordered stages to the user and confirm the scope.
3. Write a small, idempotent wizard using the target project's conventions.
4. Open or describe the relevant URL before asking for a value, hide secrets, and confirm irreversible actions.
5. Validate syntax and static value routing without executing the wizard.
6. Explain how to run it and where it writes results.

Do not generate a wizard for actions the agent can safely perform itself. Never place credentials in source or logs.
