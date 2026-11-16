# Livius Chat

Chat, voice, streaming and mini-games with friends. For Windows PC and Android.

Similar to Discord, but with no central server: devices connect directly to each other (peer-to-peer). No account needed.



https://github.com/user-attachments/assets/e2de37fa-3efa-475c-b355-bdd64b168cb0



*Versione italiana: [README.it.md](README.it.md)*

## Features

**Groups and chat**
- Groups with text and voice channels
- Join with a code or an invite file
- Replies, @mentions, @everyone, reactions, emoji
- Pinned messages, search, typing indicator
- File sharing
- Status (online, away, do not disturb, invisible) with a custom message
- Notifications and unread badges

**Voice and video**
- Voice chat with noise suppression
- Push-to-talk, mute, per-user volume
- Screen or window sharing, 720p/1080p at 30/60 fps
- PC audio sharing
- Webcam with blurred or custom background
- Shared soundboard (mp3, wav, ogg, flac, m4a)
- In-game overlay (PC)
- Calls stay active while you browse other groups

**Friends**
- Personal friend code
- Private chats and calls
- Messages are delivered even if your friend is offline

**Group management**
- Automatic host: if the host leaves, another member takes over
- Roles: owner, moderators, members
- Temporary or permanent kick

**Mini-games**
- The Monster (3D, multiple maps)
- The Infiltrator (words and voting)

**Multiple devices**
- PC and phone on the same account, linked with a code
- Profile, groups and friends stay in sync

**Languages**
- English, Italian and Spanish
- Follows the system language, can be changed in Settings

**Android**
- Phone-first interface
- All camera lenses
- Phone screen sharing
- Full-screen incoming calls
- Screen turns off when you hold the phone to your ear
- Touch joystick in games
- Runs in the background

## Discord vs Livius Chat

| | Discord | Livius Chat |
|---|---|---|
| Servers | Central | None, peer-to-peer |
| Account | Email and password | Just a name |
| Messages | On the servers | On the members' devices |
| Games | External | Built in |

Independent project, not affiliated with Discord. Original graphics and sounds.

## Technical

**Language**: Rust.
**Main libraries**: egui/eframe (UI), iroh and iroh-gossip (networking), Opus (voice), H.264 (video), RNNoise (noise suppression).

**Network**
- Each device has its own identity, generated locally.
- Direct, encrypted connections (QUIC). When that isn't possible, traffic goes through a relay that only sees encrypted data.
- The group code is used to find who is online. There is no central list of groups.
- Messages are signed by their author.
- The group state is copied to every member, so the host can change without losing anything.

**What travels and how**

| What | How |
|---|---|
| Messages and reactions | To the whole group, signed |
| Voice | Directly between members |
| Screen and webcam | H.264, straight to viewers |
| Files and sounds | From the sender, verified by hash |
| Messages to offline friends | Encrypted, read when they open the app |

**Profile and export**
- Your profile stays on your device.
- To move it: the device already set up shows a temporary code, the other one enters it and receives the profile over a direct encrypted connection.
- From then on the devices stay in sync, still without servers.

## Install

- Windows: `livius-chat.exe`
- Android: `livius-chat.apk` (Android 9+)

## Ideas and feedback

Ideas, suggestions and advice are welcome: open an [issue](../../issues) or start a discussion.
