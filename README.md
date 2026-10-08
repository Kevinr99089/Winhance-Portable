# Winhance Portable

🇫🇷 [Français](READMEfr.md) · 🇬🇧 [English](README.md)

A single web page, designed for the phone, that builds an **`autounattend.xml`** file from the settings catalog of [Winhance](https://github.com/memstechtips/Winhance). Everything is set by thumb, at your own pace, with no PC and nothing to install.

**Live page:** <https://kevinr99089.github.io/Winhance-Portable/>

> The page interface is in **French**. This document gives the English equivalent of each label in parentheses.

> Personal, unofficial project. It is not affiliated with Winhance or its author. See [License and credits](#license-and-credits).

---

## What the page does

The page **does not run anything**. It assembles an XML file. The actions take place later, at the first startup of Windows, when the file is used as the `autounattend.xml` of the installation.

### The catalog

| Content | Count |
|---|---|
| Winhance settings (10 tabs) | 420 |
| Windows apps to remove | 56 |
| Windows capabilities to remove | 10 |
| Windows features to disable | 7 |
| Apps to install (winget) | 182 |
| “Install Winhance” shortcut on the desktops | 1 |

Settings tabs: Privacy (90), Gaming and performance (107), Explorer (87), Power (48), Taskbar (28), Notifications (15), Updates (14), Start menu (14), Theme (10), Sound (7).

Names and descriptions are in French where Winhance translates them, and in English otherwise.

### How to read the controls

- **Settings**: three states. **–** changes nothing (Windows keeps its state), **On** applies the “enabled” value of the described function, **Off** applies the “disabled” value. Lists and the AC/Battery (Secteur/Batterie) fields are ignored as long as they stay on “–”.
- **Windows apps** (*Apps Windows*): box checked = the app is **removed**. Unchecked = it stays. It never reinstalls anything.
- **External apps** (*Apps externes*): box checked = the app is **installed** (winget). Unchecked = nothing happens. It never uninstalls anything.

### Buttons and navigation

A bar at the bottom of the screen, within thumb reach:

- **Menu**: Winhance recommended settings for all tabs, load a file, clear the current tab, reset everything, help.
- **Recommandé** (Recommended): applies Winhance's choices to the **current tab** only.
- **Défaut Windows** (Windows defaults): restores the current tab to **Windows' original values**. On the app tabs it becomes “Tout décocher” (Uncheck all). There is deliberately no global version.
- **XML**: opens the generated file, with Download, Copy and Select. A counter shows the number of choices.

Other elements: search across all options, tabs pinned at the top, two columns in landscape, collapsible notes, short messages above the bar. Choices are remembered in the device's browser.

### Loading an existing file

The “Charger un fichier” (Load a file) button, in the Menu, accepts:

- a **`.winhance`** file (a configuration exported by Winhance);
- an **`autounattend.xml`** created by Winhance or by this page.

The page ticks the settings it recognizes. You edit them, then get an XML back. Some elements of a Winhance autounattend may not be recognized: the message shown tells you how many were.

### Specific settings

- **Power plan**: Power saver, Balanced, High performance, Ultimate performance, or the **Winhance plan** (created from Ultimate performance). Windows' hidden power settings are unlocked before the values are applied.
- **Edge and OneDrive**: removed with Winhance's own removal scripts, embedded in the XML.
- **Teams and Xbox**: Winhance's fixes are added when you remove these apps (stopping the Teams processes, redirecting the Game Bar).
- **Defer updates until the desktop** (“Différer les mises à jour jusqu'au bureau”, in the “Mises à jour” tab): blocks Windows Update during OOBE without touching the network or the Microsoft account, then re-enables it at the first sign-in and starts a scan. **Unofficial method**, untested. On recent ISOs, the “Update later” button in OOBE also does the job.

---

## Usage

1. Open the page, pick a tab and set what you want (or use **Recommandé**).
2. Move between tabs. The counter in the bottom bar follows your choices.
3. Open **XML**, then **Télécharger** (Download), or **Copier** (Copy) and paste the content into a text file.
4. Save the file as **`autounattend.xml`** and place it at the **root** of the Windows installation ISO or USB drive.
5. Start the installation. The actions run at the first sign-in.

**Always test in a virtual machine** before using a real machine.

---

## What the XML contains

- a minimal **windowsPE** pass (license acceptance), which ensures the file is copied by the installer;
- a **specialize** pass, only if the “Defer updates” box is checked;
- an **oobeSystem** pass with **first-startup commands** (`FirstLogonCommands`): registry values, scheduled tasks, power settings, app removal, winget installs;
- an **Extensions** section that embeds the PowerShell scripts needed (Edge, OneDrive, fixes, script-based settings). They are extracted from `C:\Windows\Panther\unattend.xml` at first startup, as Winhance does.

---

## Known limitations

- **Not tested on Windows.** The tests cover the page logic, XML validity and reloading of choices. The PowerShell has not been executed.
- The generated XML is **simpler than Winhance's**: a series of first-startup commands, not its full script. It is therefore not byte-for-byte identical.
- **No disks or accounts**: partitioning, account creation and language are not handled. The network and the Microsoft account are left untouched.
- **User** settings (HKCU) apply to the first account that signs in.
- Script extraction requires the file to be used as **the installation's `autounattend.xml`** (copied to `C:\Windows\Panther`). Applied after the fact, this mechanism may not work.
- **winget** installs, the Winhance shortcut and the update scan need a **network connection** at first startup.
- **Service** settings go through the registry `Start` value: they take effect after a restart.
- Notification-area icon settings only affect the icons already present at first startup.
- Some settings exist only on Windows 11, others only on Windows 10 (indicated in their description).
- Removing **Edge** can make Windows unstable, as Winhance warns.
- Reloading the XML does not recover **every** choice: about 13 out of 473 are lost in a round trip with the full preset.
- The “Show all pins by default” option relies on a registry value documented by Microsoft, and could not be compared with Winhance's code.

---

## Privacy

Everything happens in the browser. The page contains no external resources and sends no data. Choices are kept locally (browser storage) and loaded files are read on the device.

---

## License and credits

Winhance is the work of Marco du Plessis and its contributors, released under the **PolyForm Shield 1.0.0** license. The settings catalog, the French translations and the embedded scripts (Edge and OneDrive removal, fixes) come from it.

Required Notice: Copyright (c) 2025 Marco du Plessis (https://github.com/Jeyloh/Winhance)

- Winhance license: <https://polyformproject.org/licenses/shield/1.0.0>
- Original project: <https://github.com/memstechtips/Winhance>

This project is also distributed under the **PolyForm Shield 1.0.0** license (see the [`LICENSE`](LICENSE) file), which carries over Winhance's copyright notice above. This page is a personal, unaffiliated tool that is not meant to replace Winhance. For the full application, use Winhance itself.
