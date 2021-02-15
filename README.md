# GlobalFileMenu GNOME Shell Extension

## About:
This project is a fork of [gonzaarcr/Fildem](https://github.com/gonzaarcr/Fildem) which is a fork of gnomehud with the addition of a global menu bar. This is a prototype, and GTK-4 plans to remove exporting of appmenu module, so compatibility with GTK-4 will likely never work barring upstream changes.

![File-Menu](https://user-images.githubusercontent.com/19943481/95288612-1d272a80-083f-11eb-9400-be88f61e054d.png)


## Installation

#### Install dependencies:

Ubuntu:
```
sudo apt install libbamf3-dev bamfdaemon libkeybinder-3.0-dev appmenu-gtk2-module appmenu-gtk3-module unity-gtk-module-common
```
Arch:

Note upstream tested Arch in VM, compatibility is uncertain. 
```
pacman -S bamf appmenu-gtk-module libkeybinder3 libdbusmenu-gtk2 libdbusmenu-gtk3 libdbusmenu-qt5
```

#### Install Python dependency:
```
pip3 install fuzzysearch
```

### Configure GTK:

- For GTK-2.0, make sure the file `~/.gtkrc-2.0` (or similar for your config. I use `~/.config/gtk-2.0/gtkrc`) exists and append `gtk-modules="appmenu-gtk-module"`
- For GTK-3.0, make sure the file `~/.config/gtk-3.0/settings.ini` exists and has the following line `gtk-modules="appmenu-gtk-module"` under `[Settings]`. If it doesn’t exist create it and paste the following:
```
[Settings]
gtk-modules="appmenu-gtk-module"
```

### Clone repo:
`git clone https://github.com/samlehman617/gnome-shell-extension-filemenu`

### Move extension directory
Move our extension code and metadata to the GNOME Shell Extensions directory.
`mv gnome-shell-extension-filemenu/globalfilemenu@samlehman.dev ~/.local/share/gnome-shell/extensions`

### Move executable
Move this repo to somewhere in your system PATH (I use `~/Applications`).
`mv gnome-shell-extension-filemenu ~/Applications`

## Usage
- Run by launching `run.sh` OR configure your system to launch `run.sh` on startup (see below).
- Show HUD with [ALT]+[SPACE]
- Hover the top panel in gnome-shell to reveal the menu

## Customization
 - Always Show Menu (default: show on hover): change `FORCE_SHOW_MENU` in `globalfilemenu@samlehman.dev/extension.js` to `true`, and reload GNOME-Shell (`Alt+F2, r`).
 - Always Show AppMenu Button: change `SHOW_APPMENU_BUTTON` in `globalfilemenu@samlehman.dev/extension.js` to `true`, and reload GNOME-Shell (`Alt+F2, r`).
 - Fix Space Between Buttons: Some GNOME-Shell themes have a small spacing between the buttons. This can make the buttons easy to miss and unfocus our window if not maximized. To fix, add the following somewhere in your `gnome-shell.css` theme: 
```
#panel #panelLeft {
  spacing: 0px; }
#panel #panelLeft .panel-button {
  spacing: 0px; }
```


## Running at startup

Configure `autostart` to automatically run `run.sh` at system startup" by creating a `.desktop` file in your `autostart` directory (e.g. `~/.config/autostart/globalfilemenu.desktop`) containing the following:
```
[Desktop Entry]
Type=Application
Name=GlobalFileMenu
Exec='[SOME APPLICATION DIRECTORY IN YOUR SYSTEM PATH]/GlobalFileMenu/run.sh'
StartupNotify=false
Terminal=false
```

## Compatibility
This extension can only work with programs that have exported their appmenu module. Many programs do not do this, and support for doing so will be removed in GTK-4.0. Expect fewer programs to be compatible as they migrate to GTK-4.0.

[The wiki has a list of working apps](https://github.com/samlehman617/gnome-shell-extension-filemenu/wiki/Using#state-of-the-apps)

## Troubleshooting

See [this discussion](https://github.com/gonzaarcr/Fildem/discussions/33). Please do not open an issue upstream. Either use the existing discussion or open an issue on this repo. 


## Credits
Forked from [gonzaarcr/Fildem](https://github.com/gonzaarcr/Fildem). [![Buy Him A Coffee](https://img.shields.io/badge/buy%20me%20a%20coffee-donate-yellow.svg)](https://buymeacoffee.com/gonza)
