# Keel for Claude Code

Lets Claude ask [Keel](https://rptxsoftware.com/keel/) why a build or test is slow:
what Keel lowered and why, what is loading the PC, and (for timing runs) steering
off for a while. It runs `keelctl mcp`, so it needs Keel installed: from the Microsoft Store
on Windows, which puts `keelctl` on the PATH; the .deb or .rpm on Linux
(`/usr/bin/keelctl`); on a Mac, Keel.app with **Settings → keelctl in Terminal**
switched on (`/usr/local/bin/keelctl`). It sends nothing anywhere.

    /plugin marketplace add rptxsoftware/keel-plugin
    /plugin install keel@rptx

Without the plugin: `claude mcp add keel -- keelctl mcp`
(on a Mac without the switch: `claude mcp add keel -- /Applications/Keel.app/Contents/MacOS/keelctl mcp`)

Tools: `keel_status`, `keel_work`, `keel_why`, `keel_missed`, `keel_actions`,
`keel_stalls`, `keel_steer_off`.

## What it runs, reads and changes

- **Runs** one program, `keelctl mcp`, which Keel installs. Nothing is downloaded, and the
  plugin holds no code of its own: a skill and this one command.
- **Reads** what Keel sees on this PC: the names, command lines, CPU use and priority of
  running processes, and what Keel did about them. Claude gets what it asks for, in the session.
- **Reaches** only Keel itself, on this PC (127.0.0.1). No other host, no telemetry.
- **Changes** one thing, and only when asked: `keel_steer_off` switches Keel's steering off
  for the seconds given, and Keel switches it back on by itself.
