# Claudio

All your Claude Code sessions in one window: every session in a list on the left, and a real `claude` console per session on the right. Several sessions run at the same time; one is shown, the others keep running in the background.

**[Download the latest version](https://github.com/nicolasdev/claudio-releases/releases/latest)** for Windows or macOS.

![Claudio with its list of sessions, dark theme](images/claudio-dark.png)

> Claudio is an independent project. It is not affiliated with or endorsed by Anthropic. Claude and Claude Code are products of Anthropic.

## Features

- **Every session in one list**, grouped by project, with its title, git branch, size and pull request number. The search ignores case and accents.
- **Real consoles**: each session runs the `claude` CLI itself, not a re-implementation, so everything you know from the terminal works the same.
- **Activity at a glance**: a dot marks the consoles open in Claudio, and turns into a spinning half circle while Claude is working. The window title and the taskbar (Windows) or Dock (macOS) icon show when Claude is working in at least one session.
- **Rename** a session: the name is the one `/rename` sets, so `claude --resume` shows it too.
- **Start a new session** in a recent folder or any other folder.
- **Unload** a conversation to free the memory of its `claude` process.
- Dark, light or system **theme**, adjustable **font sizes**, interface in **English, French and Spanish**.

![The same list in the light theme](images/claudio-light.png)

## Install

You need Claude Code installed and logged in: `claude` must work in a terminal.

Download the installer for your system from the [latest release](https://github.com/nicolasdev/claudio-releases/releases/latest):

| System | File |
|---|---|
| Windows (x64) | `Claudio-<version>-win-x64.exe` |
| macOS, Apple Silicon | `Claudio-<version>-mac-arm64.dmg` |
| macOS, Intel | `Claudio-<version>-mac-x64.dmg` |

The installers are not code-signed yet, so the first launch shows a warning:

- **Windows**: on "Windows protected your PC", click **More info**, then **Run anyway**.
- **macOS**: the first launch is blocked. Open **System Settings → Privacy & Security** and click **Open Anyway** next to the message about Claudio.

## Usage

| Action | How |
|---|---|
| Resume a session | Click it in the list |
| New session | **+** button or `Ctrl+N` (`⌘N` on Mac), then a recent folder or "Other folder…" |
| Rename | `F2`, double-click the title, or **⋯** → Rename |
| Unload a conversation | **⋯** → Unload conversation: stops its `claude` process and frees its console |
| Collapse a project | Click its name in the list |
| Resize the list | Drag the separator (the width is remembered) |
| New line in the prompt | `Shift+Enter` |
| Copy / paste | `Ctrl+C` on a selection / `Ctrl+V` (`⌘C` / `⌘V` on Mac) |
| Theme, text size, language | Settings (⚙) |
| Keyboard only | `Tab` to the list, arrows to move, `Enter` to open, `F2` to rename, `Shift+F10` or the Menu key for the session menu |

"folder not found" means the session's original folder no longer exists on this machine. Claude Code only resumes a session from its original folder, so restore or recreate that folder at the same path.

Claudio finds your sessions in `~/.claude`, or in `$CLAUDE_CONFIG_DIR` when that variable is set. Settings (⚙) → "Add folder…" adds other Claude configuration folders, for example `~/.claude-work` if you use several accounts.

## Privacy

- Claudio runs on your machine and sends nothing over the network itself. The `claude` consoles it starts talk to Anthropic exactly as they do in a terminal.
- It reads the session transcripts in your Claude configuration folders. It writes to them only to rename a session, by appending one line.

## Good to know

- Claudio relies on parts of Claude Code that are internal and undocumented: the transcript format, the record written by `/rename`, and the terminal title Claude sets while it works. A Claude Code update can break the list, renaming or the activity indicator until Claudio is updated.
- Do not open in Claudio a session that is already open in another terminal: two `claude` processes would write to the same session.
- Closing Claudio stops the running sessions. It asks for confirmation only when Claude is working in at least one of them.
- Linux is not supported yet.

## License

Claudio is freeware: free to use, for personal or commercial purposes. See [LICENSE](LICENSE).
