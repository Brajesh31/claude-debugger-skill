# Debugger Implementation Playbook

## Intake
- Capture the exact error message, stack trace, environment, and recent changes.
- Record expected behavior and actual behavior.
- Identify whether the failure is deterministic, intermittent, or environment-specific.

## Reproduction
1. Reduce the failure to the smallest reproducible case.
2. Record inputs, configuration, dependency versions, and execution steps.
3. Add a regression test before changing behavior when practical.

## Diagnosis
- Trace the failing path from entry point to failure.
- Inspect recent commits and dependency changes.
- Check boundary conditions, null values, state transitions, async ordering, and resource cleanup.
- Use targeted logs or a debugger. Avoid broad, noisy logging.
- Form one hypothesis at a time and test it against evidence.

## Fix
- Correct the underlying cause with the smallest safe change.
- Avoid unrelated refactors.
- Preserve existing public interfaces unless the issue requires a change.
- Handle failure states explicitly.

## Verification
- Run the narrow regression test first.
- Run relevant unit, integration, and end-to-end tests.
- Check adjacent workflows for regressions.
- Remove temporary diagnostics.
- Report the root cause, changed files, tests run, and any remaining risk.

## Diagnostic Report Template
| Field | Details |
|---|---|
| Symptom | |
| Reproduction | |
| Root cause | |
| Evidence | |
| Fix | |
| Tests | |
| Residual risk | |

## Guardrails
- Do not claim a fix without reproducing or otherwise verifying the failure.
- Do not hide errors with broad exception handling.
- Do not weaken tests to make them pass.
- Do not expose secrets, tokens, or personal data in logs.
