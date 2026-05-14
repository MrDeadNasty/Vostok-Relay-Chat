# Vostok-Relay-Chat

<img width="1536" height="1024" alt="rvc2" src="https://github.com/user-attachments/assets/3fad9d17-1953-4d35-9507-befb9b201945" />

Global in-game chat for Road to Vostok. Talk to other players in real time without leaving the game.
What it does
Adds a chat overlay to the bottom-left corner of your screen. Every player running this mod connects to the same relay server — type a message and everyone online sees it.
Closed: New messages pop up as fading toasts in the corner so you never miss anything while playing. They fade out after a few seconds.
Open: Press T to open the full chat panel with scrollback history and a text input. Press T again or Escape to close.
To text again after sending a message tap the Enter Key again.
No lobby system. No friend lists. No voice chat. Just a simple global text chat — like the zone radio from STALKER.
 Features
Global chat — everyone on the relay sees every message
Passive toast view — incoming messages fade in and out while chat is closed
Full scrollback — open the panel to see message history (configurable, default 80 messages)
Auto-generated callsigns — get a random name like "GrimStalker47" on first launch, or set your own with /name
Auto-reconnect — drops and reconnects silently if the server hiccups
MCM integration — all settings configurable through Mod Configuration Menu (optional, works without it)
 MCM Settings
Requires Mod Configuration Menu (optional — the mod works with defaults if MCM isn't installed).
Identity
Display Name — your chat name (2–24 characters, or leave blank for auto-generated)
Connection
Relay Server URL — WebSocket address of the relay server DO NOT CHANGE
 Controls
Chat Toggle Key — rebindable (default: T)
Display
Show Join/Leave Messages — on/off (default: on)
Chat Window Opacity — 0.2 to 1.0 (default: 0.88)
Chat Text Size — 8 to 24 (default: 12)
Message History — 20 to 200 messages (default: 80)
Passive View
Passive Chat Display — enable/disable the fading toast popups (default: on)
Toast Duration — how long each toast stays on screen, 3–30 seconds (default: 8)
 In-Game Commands
/name YourName — change your display name
/status — show connection info
/help — list commands
Changing Your Display Name

You'll get a random callsign like "GrimStalker47" on first launch. Two ways to change it:
In-game (fastest): Press T to open chat, type /name YourNewName, press Enter. Saves automatically.
Via MCM: Open MCM → Vostok Relay Chat → Identity → Display Name. Type your name and save.
Names must be 2–24 characters. Letters, numbers, underscores, dashes, dots, and spaces are allowed. Both methods persist between sessions.
Must restart game for name change to take affect.
 Installation
Install vostok-mod-loader if you haven't already
Drop VostokRelayChat.vmz into your mods folder:
Launch the game through the mod loader
Enable the mod and click Launch Game
That's it. The relay URL is baked into the mod — no configuration needed.
 How it works
The mod adds two autoloads via the mod loader. One registers MCM settings, the other runs the chat. It creates a UI overlay on a high CanvasLayer, connects to a WebSocket relay server hosted on Cloudflare Workers (free tier), and broadcasts messages between all connected clients. No game files are modified — it's a pure autoload mod with no hooks or script replacements.
The relay server is a Cloudflare Durable Object that acts as a simple broadcast hub. It handles rate limiting, username sanitization, and connection management. The game's freeze flag is used to pause player input while the chat panel is open, matching how the game's own menu works.
 Self-Hosting
Want to run your own relay? The server code is included. You need a free Cloudflare account and Node.js 18+. Full deploy guide is in the download. Takes about 5 minutes.
Early Testing Notice

This mod is in early testing. You may encounter bugs. Known limitations and things to be aware of:
This is the first public release and has not been tested across all hardware/OS configurations
The chat UI is built entirely in code (no .tscn scenes) so visual glitches are possible on unusual display resolutions or UI scale settings
If the relay server goes down, the mod will keep trying to reconnect silently — it won't crash your game, but chat won't work until the server is back
MCM integration has been written against the documented API but has not been tested with every MCM version — if settings don't appear, the mod still works with defaults
Game updates may break compatibility — the mod reads gameData.freeze and gameData.menu for pause integration, which could change in future patches
The WebSocket connection is unencrypted beyond TLS (wss://) — don't share anything private in chat
Message history is in-memory only and resets when you close the game
 If you find a bug, please report it with deadnasty on Discord or Below.
What happened
What you expected to happen
Your game version and mod loader version
Whether you have MCM installed
The game's log file (if possible)
Feedback and bug reports help make this better for everyone.
 Requirements
Road to Vostok (Steam)
vostok-mod-loader v3.0.1+
Mod Configuration Menu (optional, for settings)
Credits
Inspired by Chernobyl Relay Chat Rebirth by Anchorpoint / TKGP.
@wyldbylli for helping test messages.
