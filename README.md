# Mora

**Change your stream's delay while you're live — without restarting the stream — and send that
one feed to several services at once.**

Mora sits between OBS and the services you stream to, holding your broadcast in memory. That
lets you add, change or remove a delay mid-stream, and publish the same delayed feed to Twitch,
TikTok, YouTube and any other RTMP server simultaneously.

## Download

### [⬇ Download the latest release →](https://github.com/dekaizen/Mora/releases/latest)

Run the installer, then launch **Mora**. It keeps itself up to date automatically.

Windows 10/11, 64-bit.

> The installer isn't code-signed yet, so Windows SmartScreen will warn you the first time.
> Click **More info → Run anyway**.

## What it does

- **Live delay control.** Up to 2 minutes by default, 5 if you raise the limit in Preferences —
  changeable while you're broadcasting.
- **Multistreaming.** Up to 8 destinations at once (Twitch, TikTok, YouTube, or any RTMP/RTMPS
  server), each on its own connection, so one service failing or reconnecting doesn't disturb
  the others.
- **Nothing is re-encoded.** Your video passes through untouched, so scenes, overlays, alerts,
  chat, VODs and clips all keep working exactly as before. Mora only shifts time.
- **Your stream keys stay on your PC**, stored in Windows Credential Manager. OBS is pointed at
  Mora with a local token, so no service key ever passes through it.
- **Optional on-screen delay counter** your viewers can see, as an OBS browser source.

## How the delay actually works

To fall behind live without stopping your output, those seconds have to come from somewhere:

- **Adding delay** replays the last few seconds to your viewers.
- **Removing delay** cuts forward to live, dropping what was buffered.

Viewers see both at the moment they happen. Mora won't pretend otherwise — an overlay can cover
the join, but it can't remove it.

## Requirements

- **OBS** publishing single-track **H.264 + AAC**, **CBR**, with a 2-second keyframe interval.
- **Twitch Enhanced Broadcasting / multitrack must be turned off.** Mora can't pass it through,
  so it refuses it with an explanation rather than quietly mangling your stream.
- Around 6000 kbps is the practical ceiling.

## Licence

Mora is paid software. A licence key is required before you can start a broadcast — there is no
trial build. One key activates one PC, and activating needs an internet connection.

A broadcast that is already running is never interrupted by a licence check.

---

This repository hosts the downloads only. Issues and questions are welcome here.
