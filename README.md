# Emilio

All your Claude Code sessions in one window: every session in a list on the left, and a real `claude` console per session on the right. Several sessions run at the same time; one is shown, the others keep running in the background.

**[Download the latest version](https://github.com/nicolasdev/emilio-releases/releases/latest)** for Windows or macOS.

![Emilio with its list of sessions, dark theme](images/emilio-dark.png)

> Emilio is an independent project. It is not affiliated with or endorsed by Anthropic. Claude and Claude Code are products of Anthropic.

## Why "Emilio"?

Each letter stands for a feature:

- **E**very session: all your Claude Code sessions in one list, ready to pick up where you left them.
- **M**obile: use Emilio from your phone or another computer, through Tailscale.
- **I**solation: start a session in a new git worktree, and delete it when you are done.
- **L**imits: your Claude usage limits under the list.
- **I**ndicators: see at a glance which consoles are open and where Claude is working.
- **O**bfuscation: hide the title of a sensitive conversation behind three stand-in words.

## Features

- **Every session in one list**, grouped by project, with its title, git branch, size and pull request number. The search ignores case and accents.
- **Open sessions apart**: the sessions with an open console are listed in an Active group above the projects, so Claude writing to them does not reorder the list.
- **Real consoles**: each session runs the `claude` CLI itself, not a re-implementation, so everything you know from the terminal works the same.
- **Activity at a glance**: a dot marks the consoles open in Emilio, and turns into a spinning half circle while Claude is working. When Claude is working in at least one session, a half circle also spins in the window title, and a dot appears on the Dock icon (macOS).
- **Several consoles side by side** in a grid, each one usable as in a terminal.
- **Rename** a session: the name is the one `/rename` sets, so `claude --resume` shows it too.
- **Start a new session** in a recent folder or any other folder, or in a new git worktree so that parallel sessions do not touch the same files. A worktree session is named after its worktree, and ⎇ marks it in the list.
- **Obfuscate** the title of a sensitive conversation: three stand-in words in italics replace it in the list and the grid, and the real title shows while the pointer is over it.
- **Unload** a conversation to free the memory of its `claude` process.
- **Delete** a conversation, or a worktree with its conversations and, if you choose, its branch.
- **Usage limits** under the list, read on demand from Claude Code's `/usage`: current session, week, and week per model.
- **Remote access** from your phone or another computer, through Tailscale: the whole Emilio, list and consoles, with a key bar and a text field made for a phone keyboard.
- Dark, light or system **theme**, adjustable **font sizes**, interface in **English, French and Spanish**.

![The same list in the light theme](images/emilio-light.png)

## Install

You need Claude Code installed and logged in: `claude` must work in a terminal.

Emilio was named Rowan up to version 2.1.1, and Claudio up to version 1.5.2. It installs alongside them and starts with default settings: uninstall Rowan or Claudio yourself once Emilio is set up.

Download the installer for your system from the [latest release](https://github.com/nicolasdev/emilio-releases/releases/latest):

| System | File |
|---|---|
| Windows (x64) | `Emilio-<version>-win-x64.exe` |
| macOS, Apple Silicon | `Emilio-<version>-mac-arm64.dmg` |
| macOS, Intel | `Emilio-<version>-mac-x64.dmg` |

The installers are not code-signed yet, so the first launch shows a warning:

- **Windows**: on "Windows protected your PC", click **More info**, then **Run anyway**.
- **macOS**: the first launch is blocked. Open **System Settings → Privacy & Security** and click **Open Anyway** next to the message about Emilio.

## Usage

| Action | How |
|---|---|
| Resume a session | Click it in the list |
| New session | **+** → New session…, or `Ctrl+N` (`⌘N` on Mac); then a recent folder or "Other folder…" |
| New session in a git worktree | **+** → New worktree…, then the repository and an optional name (spaces become dashes): Claude Code creates a branch and a folder in `<repo>/.claude/worktrees` and starts the session there |
| Rename | `F2`, double-click the title, or **⋯** → Rename |
| Unload a conversation | **⋯** → Unload conversation: stops its `claude` process and frees its console |
| Delete a conversation | **⋯** → Delete conversation…: permanently deletes its transcript; the project folder is not touched |
| Delete a worktree | **⋯** → Delete worktree… on a session in a worktree: permanently deletes its folder, its uncommitted changes and the conversations started in it; a box also deletes its branch. git must be in the PATH |
| Hide a title | **⋯** → Obfuscate title; point at the stand-in words to read the real title; **⋯** → Stop obfuscating title to show it again |
| Several consoles side by side | **⋯** → Add to grid on each session (▦ in the list marks them); **▦** next to ⚙ switches between the grid and one console; click a tile to type in it, its close button removes it from the grid |
| Collapse a project | Click its name in the list |
| Resize the list | Drag the separator (the width is remembered) |
| New line in the prompt | `Shift+Enter`, or `Ctrl+Enter` if chosen in Settings (⚙) |
| Copy / paste | `Ctrl+C` on a selection / `Ctrl+V` (`⌘C` / `⌘V` on Mac), or right-click: copies the selection, or pastes when nothing is selected |
| Paste a file path | Drag the file onto a console |
| Theme, text size, language | Settings (⚙) |
| Usage limits | Settings (⚙) → "Show the usage limits", then **⟳** under the list; point at a value for its reset time |
| Use Emilio from your phone | See [Remote access](#remote-access) |
| Keyboard only | `Tab` to the list, arrows to move, `Enter` to open, `F2` to rename, `Shift+F10` or the Menu key for the session menu |

"folder not found" means the session's original folder no longer exists on this machine. Claude Code only resumes a session from its original folder, so restore or recreate that folder at the same path.

Emilio finds your sessions in `~/.claude`, or in `$CLAUDE_CONFIG_DIR` when that variable is set. Settings (⚙) → "Add folder…" adds other Claude configuration folders, for example `~/.claude-work` if you use several accounts.

## Remote access

Emilio can be used from your phone or another computer: the same list, the same consoles. It only listens on your computer and publishes itself through [Tailscale](https://tailscale.com), a private network between your own devices, on `https://<computer>.<tailnet>.ts.net:47823`. Nothing is opened on your router or your local network.

1. Install Tailscale on the computer that runs Emilio and on your phone, and sign in to the same account on both.
2. In Emilio, click the remote access button, between ▦ and ⚙: it turns the access on and off. Its ▾ arrow opens the pairing code, the port and the connected devices. Emilio publishes itself through Tailscale; if Tailscale Serve was never enabled on your tailnet, an "Enable Tailscale Serve" button opens the Tailscale page that does it, once.
3. Scan the code under ▾ with your phone. It opens Emilio in the browser; add it to your home screen if you like. The phone stays paired.

On the phone, the list and the console each take the whole screen. A bar adds the keys a phone keyboard lacks (Esc, Tab, Shift+Tab, arrows, Ctrl+C, Enter), and the text field sends what you type, or dictate, to Claude in one go. A console open on two devices takes the size of the one used last; the other device shows that it is in use elsewhere, and a click, a mouse move or a tap takes it back. Remote devices have their own console font size, in Settings (⚙).

- A paired device can do everything you can do at the keyboard, and through Claude Code run commands on your computer. Keep the pairing code to yourself. "Disconnect devices" disconnects every device and makes the old code useless.
- The computer must stay on and awake, with Emilio open: closing its window stops the remote access. Unticking the option, or quitting Emilio, removes what Emilio published through Tailscale, and nothing else; Emilio publishes itself again when it starts.
- Tailscale's Personal plan is free for non-commercial use; check [its pricing](https://tailscale.com/pricing) for work use.

## Privacy

- Emilio runs on your machine and sends nothing over the network itself. With remote access on, it also accepts connections on this computer only, and asks Tailscale to publish them to your own devices. The `claude` consoles it starts talk to Anthropic exactly as they do in a terminal, and so does the `claude` started for a few seconds when you refresh the usage limits.
- It reads the session transcripts in your Claude configuration folders. It writes to them only to rename a session, by appending one line, and deletes them only when you delete a conversation or a worktree.

## Good to know

- Emilio relies on parts of Claude Code that are internal and undocumented: the transcript format, the record written by `/rename`, the terminal title Claude sets while it works, and the `/usage` screen. A Claude Code update can break the list, renaming, the activity indicator or the usage limits until Emilio is updated.
- Do not open in Emilio a session that is already open in another terminal: two `claude` processes would write to the same session.
- Closing Emilio stops the running sessions. It asks for confirmation only when Claude is working in at least one of them.
- Deleting a conversation or a worktree cannot be undone. Both ask for confirmation, with Cancel selected. A running console is stopped first; if Claude Code does not stop in time, nothing is deleted.
- Unloading a conversation or closing Emilio asks Claude to quit, which takes a few seconds, so that it shuts down cleanly. A session in a git worktree is stopped at once instead: on quitting, Claude Code would delete an unchanged worktree, or wait for an answer about a changed one. Its worktree stays locked until the session is resumed; to remove it by hand, run `git worktree unlock <path>` first.
- Linux is not supported yet.

## License

Emilio is freeware: free to use, for personal or commercial purposes. See [LICENSE](LICENSE).
