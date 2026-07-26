# Atlas

A local dashboard and launcher for your AI coding sessions.

Atlas scans the session stores that Claude Code and Codex keep on disk and turns them into
something you can actually navigate: projects and sessions with real names, prompt previews,
sizes and last-used times. Launch or resume any of them in your terminal with one click, read
the full conversation, search everything you have ever discussed, and keep the whole thing
tidy. It works with sessions on this machine and on remote hosts over SSH.

Everything runs locally. There is no account, no cloud, and no telemetry.

## Download

Grab the latest installer from the [Releases](../../releases/latest) page.

| Flavour | Size | Use this if |
| --- | --- | --- |
| `Atlas_x.y.z_x64-setup.exe` | ~3 MB | You already have Node.js 22+ on your PATH |
| `Atlas_x.y.z_x64-setup-full.exe` | ~26 MB | You want a self-contained install (Node bundled) |
| `Atlas_x.y.z_x64-portable.zip` | ~3 MB | You want no installer, and have Node.js 22+ |
| `Atlas_x.y.z_x64-portable-full.zip` | ~35 MB | You want no installer and nothing else to install |

Windows 10/11, 64-bit. MSI packages are published alongside the NSIS installers if you prefer
them. Atlas updates itself after the first install.

The portable builds unzip and run. Everything they generate stays in the folder, so they can
sit on a USB stick or run next to an Atlas that is already installed without touching it. They
do not update themselves: download a newer zip to upgrade.

## What it does

**Browse your sessions.** Every project you have worked in, with its sessions underneath:
names, first-prompt previews, model, git branch, size and when you last touched them. Filter
by tool or by machine, search by path or name, sort how you like.

**Launch and resume.** One click opens a session in your terminal, in the right folder, ready
to continue. Windows Terminal, Alacritty, WezTerm, ConEmu and MobaXterm are detected
automatically, or you can point Atlas at any terminal with a custom command.

**Read the transcript.** A viewer built for real transcripts, including the 750 MB ones: it
pages through them in byte windows so opening one is instant. Markdown, thinking blocks, tool
calls and subagent trees are all rendered. Pop any transcript out into its own window to
compare two side by side.

**Search everything.** Search inside one session, or across every transcript you have. Long
sessions are searched from the newest content first, and a Deep option scans every byte when
you need certainty.

**Work with remote machines.** Add a host over SSH and its sessions appear alongside your
local ones: browse, preview, search and resume them the same way. Custom ports, jump hosts and
per-host SSH keys are supported, and Atlas can generate and install keys for you.

**See what it costs.** A usage view aggregates turns, tokens and estimated cost across every
session, broken down by model and over time, for this machine and each remote.

**Find and merge forked sessions.** Rewinding a conversation, or resuming one into a new file,
leaves you with several sessions that share a history. Atlas detects those groups, tells you
which copies are fully contained in another and safe to delete, and can merge the ones that
genuinely diverged into a single session without losing a message. Rewound passages are marked
in the viewer so you can see what was superseded.

**Keep it tidy.** Rename a project folder and its sessions follow. Deleted sessions go to a
recycle bin you can restore from. Export a session as an archive, import one, or copy it to
another machine.

**Stay out of the way.** Lives in the tray, summons with a global hotkey, and has a quick
launcher for jumping straight to a session by name. Light and dark themes, a secure mode that
blurs titles and paths for screen sharing, a fully translatable interface, and a battery saver
that quiets background work when you are unplugged.

## Translations

Atlas keeps every piece of interface text in a single self-contained language file, so
translating it needs no build tools and no knowledge of the codebase. See
[translations](translations/) for the reference file and a short guide. Contributions are
welcome.

## Privacy and security

- Atlas binds to `127.0.0.1` only. Nothing listens on your network.
- Your sessions are read from disk and never leave your machine, except to the remote hosts
  you configure yourself.
- No analytics, no accounts, no phoning home. The only outbound request is the update check,
  which you can turn off.
- Updates are cryptographically signed and verified before they are applied.

## Requirements

- Windows 10 or 11, 64-bit
- Node.js 22 or newer for the lean builds (the full installer and full portable bundle it)
- Claude Code and/or Codex installed, with sessions to browse
- For remote hosts: SSH access and Node.js on the remote

macOS and Linux builds are prepared but not yet released.

## Support

Found a bug or have a suggestion? Open an [issue](../../issues).
