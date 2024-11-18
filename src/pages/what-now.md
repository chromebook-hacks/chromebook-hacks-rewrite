---
title: "So, What Now?"
---


"What now?"

That's a question that I've been asked time and time again after helping someone complete this guide. This page is a non-exhaustive guide of a bunch of things you can (but not necessarily everything you should) do.

## Anonymize your Network Traffic

Assuming you followed the reccomended instructions while unenrolling and fakemurking your chromebook, you'll have installed a few murkmod plugins. There are two that we're looking at here: `wssocks.sh` and `mac-randomizer.sh`.

Open up mush (`Ctrl+Alt+T`) and go to the plugins menu (option 4). Select "Randomize Mac Address". Just in case something messes up later, write down the text after "Current MAC:" and keep it in a safe place.

Now, select `5` to randomize the last 5 bytes of your MAC address.

If you're really, really paranoid about being tracked, you can also use wssocks to further anonymize your traffic over a proxy. Quit from the MAC Address Randomizer and select the plugins menu again. Now, select "Manage proxy connections". Press enter to accept the default proxy, if you don't want to selfhost.

After a couple of seconds, everything should load and you should be good to go. Head to your network settings and point your SOCKS5 proxy towards `localhost:1080`. You should instantly see connections popping up on your dashboard, and you'll be able to use the internet like normal.

## Take Some Screenshots

If you are familiar with the r/unixporn community, you'll know that there are two parts to a linux screenshot: the neofetch output and the terminal. We have both, so why not take a beautiful screenshot?

Head to your plugins menu and select "Run Neofetch". Get this in a screenshot and you'll be the talk of the town.

## Serialize your Chromebook

Let me get started by saying that this is not a good idea on a Chromebook that you're going to have to give back at the end of the year. This is an irreverable process and will make Google's servers permanently think your Chromebook is a completely different device. This is only provided here in the not-so-rare chance that you bought an enrolled chromebook from a reseller, and the reseller refuses to unenroll the device.

First, we're going to need another murkmod plugin. Install the following:

```
serialization-util.sh
```

Then, open the serialization utility from the plugins menu. Provide a new serial number where prompted, and your device will reboot.

## Boot from a USB (RW_LEGACY)

This is the old method of booting from a USB. Although this is compatible with most Linux distros, it might not work on Chromebook hardware. See the section below this one for other instructions.

Open MrChromebox's Firmware Utility from the plugins menu. After a short bit of loading (20 seconds or so), you'll be presented with a menu. If you want to boot from a USB drive, all you should need to do is install the RW/LEGACY firmware, and, optionally, the full UEFI firmware as well.

Then, reboot your device (`Refresh+Power`) and press `Ctrl+L` at the developer mode warning screen, with a USB drive plugged in.

## Boot from a USB (Depthboot)

Follow the instructions [here](https://eupnea-linux.github.io/docs/depthboot/requirements) to build Depthboot for your Chromebook. Make sure to input your board codename and not your `stable-channel` value into the automatic device finder. Make sure to skip step 5 and 6 of the build instructions, those will be covered here.

Got everything built? Great! Now, open mush (this one is for murkmod only) and select option `15` - "Enable dev_boot_usb". Now, reboot with the USB drive plugged in (`Refresh+Power`) and press `Ctrl+U`.

What's that? You just want to install Linux and overwrite ChromeOS? Gee, if only there were [a guide for that exact purpose](depthboot)... oh well.

## Override Admin-Set Wallpaper

Open the wallpaper manager plugin and follow the prompts, supplying the path to your new wallpaper (which should be located in your Downloads folder). You should see changes immediately. If not, reboot and log in again.

## Use Crouton

In mush, select option 13 to install Crouton. After 15 minutes or so of loading, you should be prompted for a username and password. Provide them, and setup will be completed automatically.

Then, back in mush, select option 14 to start Crouton. Wait about 30 seconds, and you'll be dropped into a shiny new XFCE desktop environment.

To switch back and forth between desktops, press `Ctrl+Shift+Alt+Back` and `Ctrl+Shift+Alt+Forward`.

## Abuse Root Access

You can easily pop open a root shell or a shell as the `chronos` user (which has sudo access) and mess with the system in virtually any way imaginable. If you're dedicated enough, you can download a prebuilt copy of gcc and make and build and install various pieces of software to your system. Murkmod contains a work-in-progress installer for Chromebrew, but it is still broken as-is.

## Torrent ~~Pirated~~ Perfectly Legitimate Content

If you installed AuroraStore, you can search up "LibreTorrent". LibreTorrent is a free and open source torrent client for Android that runs beautifully on a Chromebook. It also supports socks5 proxies, meaning that if your enterprise WiFi blocks torrent connections, you can still connect correctly.

## Visit Restricted Sites

Using Crouton, you can swap over to a full Linux desktop running XFCE. Within it, you can install firefox (`sudo apt install firefox-esr`) and then set the proxy settings to point towards wssocks (`127.0.0.1` on port `1080`).

## Install Windows/MacOS/Linux with FULL UEFI firmware

Disable WP using any of the methods for your board, then flash FULL ROM firmware using the MrChromebox script.

Now, simply flash the ISO of your OS on to your usb and plug it in.

### For you Windows chumps:

Windows needs drivers. Lots of them! Beware that this takes up a lot of space, too, so it might not be best for your 20gb EMMC Chromebook. If you still insist on running Windows for some horrible reason, go [here](https://coolstar.org/chromebook/windows-install.html) for more info. If you have money to spare, simply buy them from CoolStar.

...or you can sail the high seas. Good luck finding them.

Please note that running MacOS is only possible on 10th gen and below Intel Processors, which are not Celerons, Pentiums or Atoms. Consult the [OpenCore guide](https://dortania.github.io/OpenCore-Install-Guide/) for more (but why would you even want to run MacOS? blink twice if you're doing this against your will).