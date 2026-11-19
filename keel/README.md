# Keel for Claude Code

Teaches Claude to ask [Keel](https://rptxsoftware.com/keel/) why a build or test is slow:
what Keel lowered and why, what is loading the PC, and (for timing runs) steering
off for a while. It is one skill, and Claude runs `keelctl`, the command Keel installs. So it
needs Keel: from the Microsoft Store on Windows, which puts `keelctl` on the PATH; the .deb
or .rpm on Linux (`/usr/bin/keelctl`); on a Mac, Keel.app with **Settings → keelctl in
Terminal** switched on (`/usr/local/bin/keelctl`). Keel is free for two agents.

    /plugin marketplace add rptxsoftware/keel-plugin
    /plugin install rptx-keel@rptx

The same commands as tools, for any MCP client: `claude mcp add keel -- keelctl mcp`
(on a Mac without the switch: `claude mcp add keel -- /Applications/Keel.app/Contents/MacOS/keelctl mcp`)

Commands the skill uses: `keelctl status`, `work`, `why`, `missed`, `actions`, `stalls`,
`steer off --for`.

## Things to ask

- "Why is this cargo build so slow?"
- "What is loading this PC right now?"
- "Time the test suite with Keel's steering off while it runs."

## What it runs, reads and changes

- **Runs** nothing by itself. The skill says when to run `keelctl`, and Claude runs it in
  the shell it already has, asking as it does for any command. The plugin holds no code.
- **Reads** what Keel sees on this PC: the names, command lines, CPU use and priority of
  running processes, and what Keel did about them. Claude gets what it asks for, in the session.
- **Reaches** nothing on the network. These commands talk to Keel on this PC (127.0.0.1)
  and to nothing else.
- **Changes** one thing, and only for timing: `keelctl steer off --for` switches Keel's
  steering off for the seconds given, and Keel switches it back on by itself.
