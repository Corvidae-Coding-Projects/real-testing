# Real Testing

A skill for coding agents that verifies software by building and running it,
operating its real interfaces, exploring varied inputs, and preserving
reproducible failures.

**Build it. Run it. Operate the changed feature. Explore how it fails. Preserve
what you discover.**

## Install and use

Install with the GitHub CLI:

```sh
gh skill install Corvidae-Coding-Projects/real-testing real-testing
```

Or copy `skills/real-testing/` into your agent's skills directory. Keep
`SKILL.md`, `agents/`, and `assets/` together. The agent needs access to the
program's build tools, runtime dependencies, and interface.

For an agent that supports named skills, ask:

```text
Use $real-testing to verify this change. Build and run the program, operate
the changed feature through its real interface, explore boundary and invalid
inputs, and preserve any confirmed failures as replayable regressions.
```

You can also give an agent `SKILL.md` directly and ask it to follow the workflow.

## Workflow

1. **Define the contract.** Specify observable behavior and expected results
   before executing checks.
2. **Build and launch.** Run the current version with its actual dependencies
   and isolated test data.
3. **Operate the feature.** Exercise the interface its users or callers use.
4. **Explore systematically.** Generate varied inputs or action sequences and
   check them against independent expectations or justified invariants.
5. **Fix and repeat.** Reproduce confirmed defects, fix them, rebuild, and rerun
   the affected checks.
6. **Preserve failures.** Keep concrete inputs, expected and observed behavior,
   prerequisites, and a command or procedure that detects recurrence.
7. **Report evidence.** State what ran, what passed or failed, what was blocked,
   and the limits of the exploration.

## Supported interfaces

| Software | How it is exercised |
| --- | --- |
| Command-line programs | Invoke the executable; check output, exit status, and artifacts. |
| APIs and services | Send real requests; inspect responses and downstream effects. |
| Web and desktop applications | Operate the changed controls; inspect displayed and saved state. |
| Libraries | Build and run a consumer of the public API. |
| Workers and pipelines | Submit actual work; observe completion and resulting artifacts. |

## Verification principles

Expected results come from requirements, documented contracts, known bugs, or
an independent reference. The program's own output does not become the oracle
just because it was produced.

Compilation, startup, and passing unit tests provide evidence. Completion also
requires observing the behavior the change promises. Existing automated checks
are run when required or useful; generated exploration remains bounded and
records its seed, configuration, and actual case count.

A missing dependency or inaccessible interface is reported as **BLOCKED**.
The skill uses the permissions already granted to the agent and calls for
isolated test data or sandboxes when operations have external effects.

The full instructions are in [SKILL.md](skills/real-testing/SKILL.md).

## License

[MIT](LICENSE). Copyright (c) 2026 Corvidae-Coding-Projects.
