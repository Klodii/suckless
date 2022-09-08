# My suckles configurations
In this repository there are all my suckless installations with relative configurations.

# How to install dwm (dinamic window manager) and st by suckless.org
## dwm dependences
```bash
$ sudo apt install libxft-dev libxinerama1 libxinerama-dev
```

## Installation
Each package have a README file with some information on the installation.

For dwm you can choose different paths:

### Using xinitrc
Copy the ./custom/.xinitrc.sample file in the home directory and rename it in `.xinitrc`
```bash
$ cp custom/.xinitrc.sample ~/.xinitrc
```
Then you have to restart your machine.

### Using xsessions
Xsessions enables you to choose witch ever window manager you want to use, in the login screen.
You can run ./custom/install_session, with sudo authorizations, to automatically install the window manager, or you can do the spets needed by yourself:
- add the `statusbar` script, this will populate the status bar with the date, internet connection and other things.
```
$ cp custom/statusbar /usr/local/bin/
```
we put the script in the bin directory because it is present in the PATH, so we can use the `statusbar` script in our `dwm.desktop` file (described in the end).
If you want to add or modify the status bar you can edit the `statusbar` script.

- now we need to add the script that actually execute dwm in `/usr/local/bin/` directory, doing so we can execute the script wherever we are (becasue the bin directory is in PATCH). Copy ./custom/.xinitrc.sample file in `/usr/local/bin/` and rename it in `startdwm`
```bash
$ cp custom/.xinitrc.sample /usr/local/bin/startdwm
```

- the last step consist in adding the dwm session to the windows manager selection (in order to select it in the login screen), copy ./custom/dwm.desktop file to `/usr/share/xsessions/`
```bash
$ cp custom/dwm.desktop /usr/share/xsessions/
```

---
I personally did the second option because with ubuntu (and two accounts) the first method didn't work.

## Add wallpaper
If you want to use a wallpaper install `xwallpaper` and designate a location to store the image you want to use ha a wallpaper, this location will be used by `xwallpaper` to render the image.

In order to make the wallpaper persistent after each login we put the xwallpaper command in the .xinitrc or startdwm file, and the path of the image is `~/.config/wallpaper.png`


# Configuration
To configure a suckless package you need to edit the `config.h` file and then compile it (`sudo make clean install`)
