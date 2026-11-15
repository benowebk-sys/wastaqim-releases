<div align="center">

# Wastaqim

**A living island for your Windows desktop.**

Keep the things you need close at hand: music, apps, files, downloads, prayer times, focus tools, and system alerts — all in a customizable desktop island with a friendly companion.

[**Download for Windows**](https://nova-tech-kit.github.io/nova-island/) · [Microsoft Store](https://apps.microsoft.com/detail/9PHV3N1V2H7M) · Free and open source under GPL-3.0

[Read this README in Arabic](README.ar.md)

![Wastaqim logo](build/icon.png)

![Wastaqim desktop island](promo/en/01-hero.png)

</div>

---

## What is Wastaqim?

Wastaqim is a lightweight desktop companion for Windows 10 and 11. Its compact island sits at the top of your screen and expands into a set of practical panels when you need them. It brings everyday information and shortcuts together without requiring you to keep switching windows.

The interface is available in **English and Arabic**, including a right-to-left layout for Arabic. You can enable or disable most features individually in Settings.

## Features

### A glanceable desktop island

- See the time, date, local weather, CPU and memory usage, upcoming meetings, and the next prayer in rotating idle views.
- Expand the island to open its panels, or use the keyboard shortcut **Ctrl + Alt + I**.
- Dock it vertically to a screen edge, hide it while an app is full-screen, and optionally integrate it with the browser address bar.
- Get compact alerts for volume, brightness, battery, keyboard state, downloads, connectivity, and other supported events.

### Music and media

- View the currently playing track, artwork, playback progress, and animated audio activity.
- See a brief track-change preview and open the floating mini player when you want playback controls close by.
- Media information and controls depend on the player and Windows media-session support.

![Media controls](promo/en/03-browser.png)

### Quick app launcher

- Pin up to 12 of your favorite installed apps.
- Launch an app or bring its existing window forward; right-click an app to open a new window when supported.
- Search the app list, reorder pinned apps, and see which pinned apps are running.

### Shelf for files and screenshots

- Drop files onto the island to keep them in a handy Shelf.
- Open a file, reveal it in its folder, drag it out, or remove it from the Shelf.
- Screenshots copied to the clipboard can appear as an alert and be added to the Shelf; temporary screenshot items expire after the configured time.

### Downloads

- Follow download progress, speed, and estimated time remaining in the island.
- Pause, resume, open, or locate supported downloads from the download panel.
- Optionally include files discovered in selected browser download folders.
- Download integration supports compatible browsers and download sources; availability can vary by application.

![Downloads](promo/en/04-downloads.png)

### Prayer and faith features

- See daily prayer times, the next-prayer countdown, and the Hijri date.
- Receive a reminder shortly before prayer and an alert at prayer time; calculation options and Hijri-date adjustment are configurable.
- During Ramadan, see the countdown to iftar or imsak when that information is available.
- Schedule on-screen reminders for Qur'an verses, dhikr, and du'a, with controls for frequency and quiet hours.
- Optional Quran Radio and other extensions may be available through the Plugins panel.

![Prayer and faith features](promo/en/06-faith.png)

### Focus, timers, and wellbeing

- Use a Pomodoro-style focus timer with configurable focus, short-break, and long-break durations.
- Get gentle reminders to drink water and rest your eyes.
- Meet the desktop companion, who can greet you, offer a morning brief, and react to focus sessions, prayer times, and other supported moments. Companion behaviors can be toggled in Settings.

### System information and smart clipboard

- Check weather, CPU and memory usage, and recent copied text from the System panel.
- Keep a local clipboard history and copy an earlier entry again.
- Smart Clipboard can recognize supported copied content such as links, calculations, and colors and offer a relevant action.
- See an indicator when another app is using the microphone or camera. Wastaqim does not record through either device.

![Smart tools](promo/en/05-smart.png)

### Themes, settings, and performance

- Choose from 13 built-in themes and adjust which panels, alerts, and companion behaviors are enabled.
- Configure startup with Windows, screen-edge placement, full-screen behavior, and other interface preferences.
- Reduce visual effects or enable battery-saving options on lower battery levels.

![Themes](promo/en/08-themes.png)

### Plugins, news, and meetings

- Browse the available plugin catalog from Settings and enable supported extensions.
- View app news when enabled.
- Add an iCalendar (iCal) feed in Settings to show upcoming meetings and reminders. Treat private calendar links as credentials and do not share them.

![Settings](promo/en/07-settings.png)

## Download and install

1. Download Wastaqim from the [official website](https://nova-tech-kit.github.io/nova-island/) or install it from the [Microsoft Store](https://apps.microsoft.com/detail/9PHV3N1V2H7M).
2. Run the installer and follow the prompts. The desktop installer may display a Windows SmartScreen warning because the installer is not code-signed; the Microsoft Store package is distributed through the Store.
3. Start Wastaqim. Press **Ctrl + Alt + I** to open or expand the island.

**Requirements:** Windows 10 or Windows 11, 64-bit.

## Build from source

You will need Node.js and npm on Windows.

```bash
git clone https://github.com/NOVA-TECH-KIT/nova-island.git
cd nova-island
npm install
npm start
```

Build Windows packages with the available npm scripts:

```bash
npm run dist           # x64 NSIS installer: release/Wastaqim-Setup.exe
npm run dist:portable  # x64 portable executable
npm run dist:store     # Microsoft Store / AppX package
```

## Privacy

Wastaqim has no account, ads, or analytics. Its settings, clipboard history, Shelf contents, and other local app data are stored on your PC. Some optional features make internet requests to retrieve information such as weather, approximate location for prayer times, app news, or plugin listings. The app does not send your clipboard contents or media details to those services.

Microphone and camera indicators report when **another app** is using those devices; Wastaqim does not access or record from them. Read the full [Privacy Policy](PRIVACY.md) for details about data handling and network requests.

## Support and feedback

Found a problem or have an idea? [Open an issue](https://github.com/NOVA-TECH-KIT/nova-island/issues) with steps to reproduce it and your Windows version. Please do not include private calendar URLs, personal files, or other sensitive information in issue reports.

## License and acknowledgements

Wastaqim is free software licensed under the [GNU General Public License v3.0](LICENSE).

Copyright © 2026 Wastaqim by Belal Mohamed.

The Qur'an font in `fonts/` (KFGQPC HAFS Uthmanic Script by the King Fahd Glorious Quran Printing Complex) is distributed under its own license; see [fonts/KFGQPC-LICENSE.txt](fonts/KFGQPC-LICENSE.txt). The font is not covered by the GPL. The Wastaqim name and supplied logo are also not covered by the GPL.
