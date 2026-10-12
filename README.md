<div align="center">

# Winhance Portable

**Build a Windows `autounattend.xml` from any device, right in your browser.**

[🇬🇧 English](README.md) · [🇫🇷 Français](READMEfr.md)

</div>

---

## What is Winhance Portable?

Winhance Portable is a single, self-contained HTML page that extends the idea behind [Winhance](https://github.com/memstechtips/Winhance) to more devices. Open it on a phone, a tablet or any computer, pick the Windows settings, apps and tweaks you want, and it generates an `autounattend.xml` file for an unattended Windows installation.

**Nothing is executed on the device where you open the page.** It only builds an XML file. The actions take place later, the first time Windows starts, when that file is used as `autounattend.xml`.

## Why Winhance Portable?

Winhance is a great tool, but it runs on Windows. Winhance Portable lets you prepare the same kind of configuration from anywhere:

- **Any device**: Android, iOS, tablet, Linux, macOS or Windows. If it has a modern browser, it works.
- **Mobile-first interface**: large touch targets, bottom dock navigation, safe-area support.
- **No installation, no server**: one `.html` file that works offline.
- **Private**: your choices stay in your browser's local storage and are never sent anywhere.

## Features

- **700+ options** spread over 12 tabs, with instant search across all of them.
- **Windows apps & features**: remove built-in apps, Windows capabilities and optional features.
- **External software**: install apps through `winget` (or the Store, Chocolatey or a direct download for a few of them).
- **Optimizations**: Privacy & Security (including Windows, Edge and Office AI features), Power (plugged-in and on-battery values), Gaming & Performance, Updates, Notifications and Sound.
- **Customization**: Windows theme, Taskbar, Start menu and File Explorer.
- **One-tap presets** for the current tab or for all tabs:
  - **Winhance recommended**: Winhance's suggested choices.
  - **Windows default**: restore Windows' original values.
- **Import** an existing `.winhance` or XML file to continue from it.
- **Export** the result: download the `.xml`, copy it, or select it.
- **Bilingual interface** (French and English), detected automatically from the device language.
- **Light and dark themes** that follow the system setting.

## How to use it

1. Open [Winhance Portable](https://kevinr99089.github.io/Winhance-Portable/) in your browser.
2. Browse the groups (**Software & Apps**, **Optimizations**, **Customization**) and their tabs, or use the search bar.
3. Set your choices:
   - **Windows apps**: checked = removed.
   - **External apps**: checked = installed.
   - **Settings**: use the switch for On/Off, or pick an option from the list.
4. Optionally apply a preset (**Winhance recommended** or **Windows default**) from the bottom bar or the menu.
5. Open the **XML** panel and download or copy the generated `autounattend.xml`.
6. Use it with your Windows installation media or setup process.

> Unchecking an app never does the opposite: an unchecked Windows app is left alone (never reinstalled), and an unchecked external app is simply not installed (never uninstalled).

## Tabs at a glance

| Group | Tabs |
| --- | --- |
| Software & Apps | Windows apps & features · External software |
| Optimizations | Privacy & Security · Power · Gaming & Performance · Updates · Notifications · Sound |
| Customization | Windows theme · Taskbar · Start menu · File Explorer |

## Good to know

- The generated file **does not handle disks or user accounts**.
- User settings (HKCU) are applied to the **first account that signs in**.
- `winget` apps, the Winhance shortcut and the update check **require a network connection**.
- A setting with no known original value (cleanup actions, for example) is not changed by **Windows default**.
- When importing a file, the parts this page does not handle (scripts, services, tasks) are ignored.
- **Always test in a virtual machine before using a real machine.** These tweaks change deep system settings.

## Credits

Winhance Portable is inspired by [Winhance](https://github.com/memstechtips/Winhance) by memstechtips, and was created as an extension of it. This is an independent project and is not affiliated with or endorsed by the original author or by Microsoft.

## Disclaimer

This tool is provided as is, without any warranty. You are responsible for the configuration you generate and for testing it before deploying it.