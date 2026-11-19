---
name: keel
description: Use when a command, build, test or dev server on this PC is slower than expected, or before timing anything, to see whether Keel lowered its priority and why, and what else is loading the machine.
---

# Keel

Keel steers the CPU priority of the work agents start, so the person's PC stays
responsive while many agents run. Tests, builds and compilers are lowered once
the PC is busy (and kept off a few CPUs when it is strained); servers and dev
servers stay at normal priority. Lowered work runs slower on purpose.

Ask Keel with `keelctl`, the command Keel installs. Every command takes `--json`.

- Slow command: `keelctl why <pid>`, or a word from its command line in place of
  the pid, says its lane, the rule that chose it, and its priority as the system
  reports it now.
- Machine feels slow: `keelctl status` (pressure, CPU, wake delay), then
  `keelctl work` for the heaviest groups of work and whose they are.
- Timing something (a benchmark, a performance test): Keel's steering skews the
  result. Run `keelctl steer off --for <seconds>` for the length of the run, ten
  minutes at most (it comes back on by itself), and say in the result that
  steering was off.
- Busy work Keel doesn't recognise: `keelctl missed`. Suggest a rule to the person;
  don't change their settings.
- What Keel changed, newest first: `keelctl actions`. The slow answers of the
  window in front: `keelctl stalls`.

Don't switch steering off for a whole session to make your own work faster:
it slows down the person's PC and the other agents on it. `keelctl quit`,
`reserve`, `focus` and `license` are the person's to run, not yours.

No `keelctl`: Keel isn't installed (https://rptxsoftware.com/keel/), or on a Mac
its **Settings → keelctl in Terminal** is off, and the command is
`/Applications/Keel.app/Contents/MacOS/keelctl`. With Keel not running, `keelctl`
watches the machine for a second and says what Keel would decide.
