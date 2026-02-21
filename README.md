This is a collection of files intended to install a close approximation of
BunsenLabs Linux on a basic command-line-only Debian Trixie system.

Bug reports are very welcome! Please visit the bunsenlabs forums:
https://forums.bunsenlabs.org/viewforum.php?id=14

Or post an issue on the GitHub repository:
https://github.com/BunsenLabs/bunsen-netinstall/issues


HOW TO USE
----------

Download the latest Debian trixie "netinstall" .iso file
and use it to install a basic cli system.

https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-13.1.0-amd64-netinst.iso

There is no longer a Debian i386 netinstall iso image.

Make sure sudo is enabled. (See "DEBIAN NETINSTALL HINTS" below.)

Boot your Debian cli system, log in and run these commands, as a normal user:
(A fresh copy of this bunsen-netinstall package will be downloaded.)

    wget https://github.com/bunsenlabs/bunsen-netinstall/archive/carbon.tar.gz
    tar -xpf carbon.tar.gz
    cd bunsen-netinstall-carbon
    ./install

The installation process will start.
Follow any prompts that appear on the screen.

You will be asked to choose between a regular "full" install, a "lite" install
and a "base" install.

The "lite" version installs slightly fewer packages and uses fewer system resources,
for example by not using composition or menu icons.
It also makes some app substitutions, notably that the web browser is dillo and
the text editor is nano.

The "base" install is a minimal set of packages just sufficient to make
a working BunsenLabs desktop. A lot of commonly used utilities have been omitted,
and dillo and nano are substituted as with the "lite" install.

Dillo has a very limited feature set but it's fast and light, and
good enough for finding online documentation.

Nano in a terminal has slightly different keyboard shortcuts from most graphical
text editors, but is usable for simple edits to configuration files.

A folder called bunsen-netinstall-logs will be added to your ~/.cache folder.
(The file bunsen-netinstall-logs/install.log will contain verbose information
about the install process.)
This folder may safely be removed if the installation was successful, and no
issues arose subsequently.

A folder /backup/bunsen-netinstall on your root file system will hold backups
of system files replaced during the install.

The script itself has been separated off from the files holding specific data
about the installation. This is intended to make customization easier. It
should not be necessary to edit "install". Even if the script is upgraded in
the future, the same config files should still work.

If you want to customize the installation process before running the installer
then use a cli editor like nano or vim to edit any of the files to your taste.
You might particularly want to look at pkgs-recs and pkgs-norecs
(or their "lite" or "base" equivalents), but there are other things
you might want to adjust, eg to install on Devuan...

FILES IN THIS COLLECTION
------------------------

README.md: this file\
LICENSE: a copy of the GPL3 license\
install: the installation script\
copyright: GNU licence statement\
greeting: message to user\
pkgs-recs: packages to install with recommends\
pkgs-norecs: packages to install without recommends\
pkgs-recs-lite: packages to install with recommends (lite package list)\
pkgs-norecs-lite: packages to install without recommends (lite package list)\
pkgs-recs-base: packages to install with recommends (base package list)\
pkgs-norecs-base: packages to install without recommends (base package list)\
sysfiles1: system files to copy in before installing packages (mainly apt-related)\
sysfiles2: system files to copy in after installing packages\
preinstall_commands: commands to run before installing packages and files\
postinstall_commands: commands to run after installing packages and files\
apt-keys: script to install the BunsenLabs Apt key\
gen_sources: commands to edit /etc/apt/sources.list\
config: sets some directory paths etc\
bunsen-netinstall-logs: folder to copy into user's ~/.cache directory

DEBIAN NETINSTALL HINTS
-----------------------

Installing Debian Trixie by the netinstall iso is similar to using the standard
Debian installer.

Two points to watch if you want to use this BunsenLabs netinstall script afterwards:

1) At the "Set up users and passwords" screen, **DO NOT** enter a password for root.
Type nothing and press "continue".
Do this again at "Re-enter password to verify".
Enter your own name and password as normal.
You will then be given 'sudo' permissions, which will be needed in the script.

2) At the "software selection" stage DESELECT EVERYTHING except "standard
system utilities".
You will have a core system only, on which the netinstall installer will add
what is needed.\
(Some software items will be marked with an asterisk, indicating that they have
been preselected. Use the up/down arrows to move, and the spacebar to toggle
selection.)
