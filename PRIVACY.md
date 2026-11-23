# Privacy and data handling

Updated: 23 November 2026.

This document describes the free Mora Windows desktop application, maintained by
[ahizechi](https://github.com/ahizechi). Mora does not require a Mora account,
subscription or payment details.

## Your stream

Mora receives the encoded video and audio from OBS or Streamlabs Desktop on your PC,
holds the stream in a local memory buffer, and sends it to the streaming destinations
you enable. It does not route your broadcast through a Mora-operated cloud relay.

The receiving platforms process and publish your stream under their own terms and
privacy policies. Custom RTMP destinations receive the stream and the credentials
needed to publish it. An unencrypted `rtmp://` connection does not protect that
traffic from others on the network path; use `rtmps://` where your destination supports it.

## Information kept on your PC

Mora uses local information to run the features you configure:

- **Credentials:** stream destinations and keys, supported sign-in tokens, chat API
  keys, and local connection secrets are stored using Windows Credential Manager.
  Credentials are sent to the relevant services when needed to authenticate or
  publish; local storage does not mean they are never transmitted.
- **Settings:** connected channel names, output preferences, chat filters, appearance,
  shortcuts, alert preferences, OBS scene rules and game-detection preferences are
  saved locally. Some display preferences may also be held in the app's WebView2 storage.
- **Chat:** Mora processes messages, usernames, user IDs, badges, emotes, moderation
  events and platform events such as subscriptions or gifts to display and filter
  your selected chats. The live chat buffer is held in memory rather than saved
  as a persistent transcript by Mora.
- **Stream health:** local diagnostics and the most recent stream summary can
  contain app/build and Windows versions, output names and hosts, connection state,
  timings, bitrate, error messages and aggregate chat/stream statistics. These
  are used to show health information and investigate problems.

The application writes rotating diagnostic logs under
`%LOCALAPPDATA%\Mora\logs`. Settings and the last-stream summary are kept in
Mora's application-data folder, normally `%APPDATA%\com.mora.app`. WebView2 may
also retain its own local application data.

Settings and saved credentials remain until replaced or removed. The most recent
saved stream summary is replaced by a later completed stream or can be dismissed.
Logs rotate according to file size rather than a fixed number of days. Closing Mora
ends its in-memory stream and chat processing; it does not delete saved settings,
credentials or logs. Uninstalling the app should not be assumed to erase all of them.

You can remove outputs and chat connections, disconnect supported sign-ins, and
revoke access or rotate keys with the relevant provider. To remove remaining local
data, close Mora, delete its app-data and log folders, and remove entries belonging
to Mora from Windows Credential Manager. Do not remove another application's entries.
Data already received by a platform or included in a broadcast remains subject to
that platform's controls and retention.

## Optional services

The connections depend on the features and providers you enable:

| Feature | Services and information involved |
| --- | --- |
| Streaming outputs | Your selected Twitch, YouTube, TikTok, Kick or custom RTMP/RTMPS destination receives your broadcast and publishing credentials. |
| Twitch chat and badges | Twitch receives channel/API requests and, if you choose to sign in, authorisation requests and tokens. Mora receives public chat, badge and account information needed for the feature. |
| YouTube chat | YouTube/Google receives the selected video or channel requests and an API key when you use key-based access. Mora receives the corresponding public chat and events. |
| TikTok chat | Euler Stream receives the TikTok username and the Euler API key you supply, and provides the chat/events Mora displays. |
| TikTok LIVE through Streamlabs | Streamlabs handles sign-in and LIVE access. Mora exchanges account/access information, stream title, game/category and audience settings to start and end the selected TikTok broadcast and obtain its publishing credentials. |
| Kick chat | Kick and its chat delivery service, Pusher, provide the selected channel's public chat and events. |
| Emotes and badges | Platform image hosts and enabled providers such as 7TV, BetterTTV and FrankerFaceZ receive requests for channel metadata and image assets. |
| Updates | Mora contacts GitHub to check for releases and download signed updates. |

Like other internet services, these providers receive connection information such
as your IP address and request metadata. Their processing, retention and any
international transfers are governed by their own policies and your relationship
with them; Mora does not set their retention periods.

Relevant policies include [GitHub](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement),
[Twitch](https://www.twitch.tv/p/en/legal/privacy-notice/),
[Google/YouTube](https://policies.google.com/privacy),
[TikTok](https://www.tiktok.com/legal/page/row/privacy-policy/en),
[Streamlabs](https://streamlabs.com/privacy),
[Euler Stream](https://www.eulerstream.com/privacy),
[Kick](https://kick.com/privacy-policy) and
[Pusher's privacy information](https://pusher.com/security/).
For other providers or a custom streaming server, check that provider's policy.

## OBS, overlays and automatic delay

Mora's local OBS connection can read scene names/current scene and apply the
setup actions you request. Optional game detection checks running processes and
local VALORANT logs or League of Legends' local game-data interface to decide
when to change the delay.

The private OBS dock, on-stream chat and delay badge are served locally. A dock or
browser-source URL can contain an access token: treat it as private. Chat displayed
in an on-stream overlay becomes part of the broadcast sent to your enabled outputs.

## Analytics and reports

Mora does not include a Mora-operated usage-analytics service or automatically
upload support reports or chat transcripts to the maintainer. The Support diagnostics
action creates a report for you to copy; it does not submit it. Mora is designed
to remove credentials from diagnostics, but review reports, screenshots, logs
and private links before sharing them anywhere.

Information you choose to publish on GitHub is public and is processed by GitHub
under its own privacy policy. This document does not cover third-party software,
platform accounts or services simply because you use them alongside Mora.
