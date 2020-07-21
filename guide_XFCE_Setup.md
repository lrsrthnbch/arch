# XFCE Setup & Customizing
This guide is ment as a collection of many different changes done to the XFCE desktop environment, be it fixes for issues or quality of life changes.

## Changelog
| Date | Comment |
| ------ | ------ |
| 2020/05/01 | created the document |

## to do
- [ ] nothing

## Fixes
### Mouse Acceleration
1. Open `vim /etc/X11/xorg.conf.d/50-mouse-acceleration.conf`
2. Enter the following values:

```
Section "InputClass"
	Identifier "My Mouse"
	Driver "libinput"
	MatchIsPointer "yes"
	Option "AccelProfile" "flat"
	Option "AccelSpeed" "0"
EndSection
```

### Fonts
- Enable RGB hinting in the xfce font settings
- install ttf-hack for Terminal

### Mouse cursor
In some applications the mouse cursor might be too big. To fix it, go into xfce4-settings and adjust the mouse pointer size from 16px to 32px, then change it back to 16px.

### Firefox scrolling
1. open about:config and search for mousewheel.acceleration
2. set `mousewheel.acceleration.start` to `-1`
3. set `mousewheel.acceleration.factor` to `20`
4. set `mousewheel.default.delta_multiplier_y` to `200`

If that doesn't work, try setting the values as followed:
```
general.smoothScroll.mouseWheel.durationMinMS : 600
mousewheel.acceleration.start : 2
mousewheel.default.delta_multiplier_x : 400
mousewheel.default.delta_multiplier_y : 400
mousewheel.default.delta_multiplier_z : 400
mousewheel.min_line_scroll_amount : 1
```
### Install app images
1. install `sudo pacman -S fuse2`
2. chmod the file: `sudo chmod +x xyz`
3. run it: `./xyz`

### motd
1. edit `nano /etc/motd`
2. add the desired message

### xfce terminal schemes
1. download a colorscheme, for example [Nord](https://github.com/arcticicestudio/nord-xfce-terminal)
2. put it into `~/.local/share/xfce4/terminal/colorschemes`
Example:
Create the file `nord.theme` in the directory above and paste:
```
[Scheme]
Name=Nord
ColorCursor=#D8DEE9
ColorForeground=#D8DEE9
ColorBackground=#2E3440
TabActivityColor=#88C0D0
ColorPalette=#3B4252;#BF616A;#A3BE8C;#EBCB8B;#81A1C1;#B48EAD;#88C0D0;#E5E9F0;#4C566A;#BF616A;#A3BE8C;#EBCB8B;#81A1C1;#B48EAD;#8FBCBB;#ECEFF4
ColorBold=#D8DEE9
ColorBoldUseDefault=FALSE
```

### Screenshot
1. Set shortcut for `xfce4-screnshooter -r -m` (-r -m captures a region and the mousepointer)

### Xfce Shortcuts
1. `xfce4-popup-whiskermenu`
2. `xfce4-session-logout --suspend`

### Xfce Panel location
1. 1080: `xfconf-query -c xfce4-panel -p /panels/panel-1/position -s "p=0;x=960;y=1056"`
2. 2560: `xfconf-query -c xfce4-panel -p /panels/panel-1/position -s "p=0;x=1280;y=1412"`

### Fingerprint (only on X230)
1. install fprintd `sudo pacman -S fprintd`
2. enroll a finger (swipe five times) `fprintd-enroll`
3. add the following line `auth		sufficient  	pam_fprintd.so` to /etc/pam.d/system-local-login, su and sudo xfce4-screensaver in the same directory **at the top of the file**

### Youtube to mp3
`youtube-dl -x -f 'bestaudio[ext=m4a]' --embed-thumbnail -o '%(title)s.%(ext)s'`

## Important packages
### TLP - battery improvements for laptops
1. install the following packages `pacman -S tlp tlp-rdw tp_smapi acpi_call`
2. enable services: `systemctl enable tlp.service`
3. enable services: `systemctl enable NetworkManager-dispatcher.service`
4. mask the following services: `systemctl mask systemd-rfkill.service`, `systemctl mask systemd-rfkill.socket`

### yay - AUR manager
1. download from git: `git clone https://aur.archlinux.org/yay.git`
2. cd into the directory: `cd yay`
3. make: `makepkg -si`

### LibreOffice
install `sudo pacman -S libreoffice-fresh libreoffice-fresh-de ttf-liberation`

### OpenSSH
1. install `sudo pacman -S openssh`
2. you might wanna configure the daemon config: `vim /etc/ssh/sshd_config`
2. enable & start: `sudo systemctl enable sshd.service`, `sudo systemctl start sshd.service`

Create ssh keypair:
1. run `ssh-keygen -t rsa` to create a keypair (press enter on pw prompt to not use one)
2. copy public key to the server: `ssh-copy-id [user]@[server]`

### zsh
1. Download via pacman `sudo pacman -S zsh`
2. Switch to zsh by running `zsh`
3. An assistent should appear. Accept the default settings
4. To make zsh the default shell, run `chsh -s /bin/zsh`
5. Change the prompt by editing .zshrc and adding the line `PROMPT="%B%F{blue}%~%f%b%B%F{magenta} > %f%b"`
6. Logout for changes to take effect

### Nextcloud
1. install required packages for storing the login password, otherwise autologin won't be possible: `sudo pacman -S gnome-keyring libgnome-keyring seahorse`
2. install nextloud `sudo pacman -S nextcloud-client`
3. set default keyring to be qithout a password

### Zathura
1. Install zathura and it's mupdf dependency: `sudo pacman -S zathura zathura-pdf-mupdf`

## Packages
This is a collection of all the packages installed in a chronological order
| package | description | usage |
| ------ | --------- | --------- |
| firefox | open source webbrowser | |
| neofetch | show info about the os and hardware | |
| git | version control system | |
| yay | AUR manager | check this guide |
| gimp | photo manipulation suite | |
| gcolor2 | color picker utility | |
| tlp | battery improvements | check this guide for further information |
| vlc | open source media player | |
| youtube-dl | YouTube downloader | |
| qbittorrent | torrent utiliry | |
| clementine | GUI music player | |
| xarchiver | compression tool with thunar integration | |
| geany | text editor / IDE | |
| bitwarden | pw manager | electron based :( install from AUR |
| ttf-hack | great monospace font | |
| nextcloud-client | frontend for cloud | |
| zathura | pdf reader | see this guide |
| calibre | e-book manager | |
| cherrytree | onenote like app for notes | install from AUR |
| discord | voice chat platform | |
| gnome-disk-utility | partition manager | |
| ntfs-3g | ntfs support | |
| hexchat | irs client | |
| unrar | unarchiver | might be necessary for xarchiver to unpack rar files |
| networkmanager-vpnc | cisco vpn plugin for network manager | |
| jdownloader2 | Download Manager | install from AUR|
| cool-retro-term-git | terminal emulator with retro effects | install from AUR |
| catfish | file finder | |
| xfce4-sensors-plugin-nvidia | plugin for displaying gpu stats in the panel | install from AUR |
