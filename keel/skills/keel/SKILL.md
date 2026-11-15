---
name: keel
description: Use when a command, build, test or dev server on this PC is slower than expected, or before timing anything, to see whether Keel lowered its priority and why, and what else is loading the machine.
---

# Keel

Keel steers the CPU priority of the work agents start, so the person's PC stays
responsive while many agents run. Tests, builds and compilers are lowered once
the PC is busy (and kept off a few CPUs when it is strained); servers and dev
servers stay at normal priority. Lowered work runs slower on purpose.

- Slow command: `keel_why` with its pid or a word from its command line says its
  lane, the rule that chose it, and its priority as the system reports it now.
- Machine feels slow: `keel_status` (pressure, CPU, wake delay), then `keel_work`
  for the heaviest groups of work and whose they are.
- Timing something (a benchmark, a performance test): Keel's steering skews the
  result. Run it with `keel_steer_off` for the length of the run (it comes back
  on by itself), and say in the result that steering was off.
- Busy work Keel doesn't recognise: `keel_missed`. Suggest a rule to the person;
  don't change their settings.

Don't switch steering off for a whole session to make your own work faster:
it slows down the person's PC and the other agents on it.
