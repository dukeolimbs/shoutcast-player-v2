# SHOUTcast Player (Improved)

A lightweight [Foundry VTT](https://foundryvtt.com/) module that plays a
SHOUTcast/Icecast audio stream directly from the Token Controls toolbar — with
proper connection state management and automatic retrying.

Handy for running live music (e.g. a [Mixxx](https://mixxx.org/) broadcast) or
any internet radio stream into your game session without leaving Foundry.

## Features

- 🎵 Play/stop a SHOUTcast/Icecast stream from a toolbar button (📻 radio icon).
- 🔄 **Connection state machine** — clear status for _Connecting_, _Live_,
  _No Signal_, and _Connection Failed_.
- ⏳ **Auto-retry** — when the server is reachable but not yet broadcasting
  (e.g. your DJ software isn't live), it retries every 15 seconds automatically.
- 🔊 **Per-client volume** — each player controls and remembers their own volume.
- 📡 **GM sync** — when the GM presses Play/Stop, connected clients follow along
  via the module socket.

## Installation

### From manifest URL (recommended)

In Foundry, go to **Add-on Modules → Install Module** and paste this manifest URL:

```
https://github.com/dukeolimbs/shoutcast-player-v2/releases/latest/download/module.json
```

### Manual

Download the latest `module.zip` from the
[Releases](https://github.com/dukeolimbs/shoutcast-player-v2/releases) page and
extract it into your Foundry `Data/modules/` folder as `shoutcast-player-v2`.

## Usage

1. Enable the module in **Manage Modules**.
2. Open **Game Settings → Configure Settings → SHOUTcast Player (Improved)** and
   set your **Stream URL**, e.g. `http://your.stream.ip:8000/stream`.
   (This is a per-client setting.)
3. Click the **📻 radio button** in the Token Controls toolbar to open the player.
4. Press **Play**. The status bar shows the live connection state; adjust volume
   with the slider.

### Connection states

| State | Meaning |
| --- | --- |
| **Connecting…** | Attempting to reach the stream (8s timeout). |
| **LIVE** | Audio is playing. |
| **No Signal — retrying…** | Server reached, but no audio source yet (e.g. broadcaster not live). Auto-retries every 15s; a **Retry Now** button is also available. |
| **Connection Failed** | Server unreachable. Use **Retry** once it's back up. |

## Compatibility

- Foundry VTT **v14+** (verified on 14.359).

## Development

This is a plain JS/CSS/Handlebars module — no build step. For local development,
symlink the repo into your Foundry `Data/modules/` folder:

```bash
ln -s /path/to/shoutcast-player-v2 ".../FoundryVTT/Data/modules/shoutcast-player-v2"
```

Releases are published automatically by GitHub Actions on version tags — see
[`.github/workflows/release.yml`](.github/workflows/release.yml).

## License

[MIT](LICENSE) © Owen (dukeolimbs)
