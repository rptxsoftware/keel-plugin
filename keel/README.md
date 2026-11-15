# Keel for Claude Code

Lets Claude ask [Keel](https://rptxsoftware.com/keel/) why a build or test is slow:
what Keel lowered and why, what is loading the PC, and (for timing runs) steering
off for a while. It runs `keelctl mcp`, so it needs Keel installed: from the Microsoft Store
on Windows, which puts `keelctl` on the PATH; the .dmg on macOS, then Keel's Settings →
"keelctl in Terminal"; or the .deb or .rpm on Linux (`/usr/bin/keelctl`). It sends nothing
anywhere.

    /plugin marketplace add rptxsoftware/keel-plugin
    /plugin install keel@rptx

Without the plugin: `claude mcp add keel -- keelctl mcp`

Tools: `keel_status`, `keel_work`, `keel_why`, `keel_missed`, `keel_actions`,
`keel_stalls`, `keel_steer_off`.
