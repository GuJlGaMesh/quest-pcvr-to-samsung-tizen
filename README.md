# Play Beat Saber on Quest 3 and show it on a Samsung Tizen TV

[العربية](README.ar.md) · [中文](README.zh.md) · [English](README.md) · [Français](README.fr.md) · [Русский](README.ru.md) · [Español](README.es.md)

**One player, two screens.** In this setup, the Windows PC runs Beat Saber. Virtual Desktop streams the VR game to the player's Quest 3. In parallel, Sunshine captures the PC desktop and streams it over the home network to Moonlight on a Samsung BU8000. Spectators see whatever the PC monitor shows.

**What you need.** A Windows gaming PC with the PC version of Beat Saber, a Quest 3 already set up for PCVR with Virtual Desktop, and a Samsung BU8000 on the same home network. The tested TV ran Tizen 6.5. The gaming PC was connected by Ethernet. A separate Windows computer was used to install the TV app.

## Set it up once

1. **On the gaming PC**, install [Sunshine for Windows](https://github.com/SunshineStream/Sunshine/releases/latest). Open its [local settings page](https://localhost:47990) on that PC and create a username and password. Keep the default **Desktop** entry in the list of applications.
2. **On the TV**, open **Apps** and enter **12345** to open the developer menu. Enable **Developer Mode**, set **Host PC IP** to the LAN address of the computer you will use to install Moonlight, then restart the TV if you changed the setting. In the tested setup this was the installation computer's address. [Moonlight Tizen installation guide](https://github.com/brightcraft/moonlight-tizen/wiki/Installation-Guide)
3. **On the installation computer**, download the standard **Moonlight.wgt** from the [Moonlight Tizen releases](https://github.com/brightcraft/moonlight-tizen/releases). Use **Apps2Samsung** to install it on the TV. The tested installation reused a Samsung Partner certificate that already covered the TV. For a first-time certificate, follow the installer's prompts. [Apps2Samsung](https://github.com/Apps2Samsung/Apps2Samsung)
4. **On the TV**, open Moonlight and select the gaming PC. If needed, add its Ethernet LAN address manually. Moonlight displays a PIN. On the gaming PC, open Sunshine's settings, select the TV's request on the **PIN** page, and enter that code. This pairs the TV with the gaming PC.

With the Apps2Samsung CLI for Windows, run this from the folder containing the CLI and the widget. Replace `TV_IP` and `INSTALL_PC_IP` with the two LAN addresses.

```powershell
.\apps2samsung-cli.exe install .\Moonlight.wgt --tv TV_IP --local-ip INSTALL_PC_IP
```

## When you want to play

Start the PC version of Beat Saber using Virtual Desktop on Quest 3. Check that the game view you want to share is visible on the PC monitor. On the TV, open **Moonlight → gaming PC → Desktop**. If spectators see the Windows desktop, check what is visible on the captured monitor first.

**Observed in this setup.** The player reported running Beat Saber. Sunshine confirmed that the BU8000 paired and started a session using H.264 hardware encoding on an RTX 3070, with 60 fps requested and stereo audio capture. The exact spectator window and end-to-end latency were not recorded.
