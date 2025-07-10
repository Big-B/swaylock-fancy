swaylock-fancy
============

This is an swaylock bash script that takes a screenshot of the desktop, blurs the background and adds a lock icon and text

![screen shot of lockscreen](https://raw.githubusercontent.com/Big-B/swaylock-fancy/master/screenshot.png)

Dependencies
------------
* <s>[i3lock-color-git](https://github.com/eBrnd/i3lock-color)</s>
* [i3lock-color-git](https://github.com/Raymo111/i3lock-color) - this is a fork of i3lock-color that is kept up to date with i3lock
* imagemagick
* bash
* awk
* jq
* util-linux
* grim
* wlr-randr

Optional Dependencies
---------------------
* wmctrl

Installation
------------

To install swaylock-fancy manually, git clone the repository:

    git clone https://github.com/Big-B/swaylock-fancy.git

Then change to the directory and run make.

    cd swaylock-fancy
    sudo make install

### The following distros have packages you can use to install:
* Arch Linux: https://aur.archlinux.org/packages/swaylock-fancy-git/

Usage
-----

    swaylock-fancy [options]

    Options:
        -h, --help       This help menu.

        -d, --desktop    Attempt to minimize all windows before locking. Requires wmctrl.

        -g, --greyscale  Set background to greyscale instead of color.

        -p, --pixelate   Pixelate the background instead of blur, runs faster.

        -f <fontname>, --font <fontname>  Set a custom font.

        -t <text>, --text <text> Set a custom text prompt.

        -l, --listfonts  Display a list of possible fonts for use with -f/--font.
                         Note: this option will not lock the screen, it displays
                         the list and exits immediately.


    The following options are passed directly to swaylock:
        -F, --show-failed-attempts    Show current count of failed authentication attempts.

        -e, --ignore-empty-password   When an empty password is provided, do not validate it.

        -K, --hide-keyboard-layout    Force hiding the current xkb layout while typing,
                                      even if more than one layout is configured or the
                                      show-keyboard-layout option is set.

        -L, --disable-caps-lock-text  Disable the Caps Lock text.

        --daemonize                   Detach from the controlling terminal after locking.

example: ```swaylock-fancy -gpf Comic-Sans-MS -- scrot -z```

Extras
------

The lock screen in action:

![lockscreen animation](https://raw.githubusercontent.com/Big-B/swaylock-fancy/master/action.gif)

To use this script you can set a hotkey in your window manager to run the lock
command. This is what it would look like in your sway config:
```
    exec swayidle -w \
        timeout 300 'swaylock-fancy' \
        timeout 600 'swaymsg "output * dpms off"' \
            resume 'swaymsg "output * dpms on"' \
        before-sleep 'swaylock-fancy'
```
