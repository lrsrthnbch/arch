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
´´´
Section "InputClass"
	Identifier "My Mouse"
	Driver "libinput"
	MatchIsPointer "yes"
	Option "AccelProfile" "flat"
	Option "AccelSpeed" "0"
EndSection
´´´

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

### zsh
1. Download via pacman `sudo pacman -S zsh`
2. Switch to zsh by running `zsh`
3. An assistent should appear. Accept the default settings
4. To make zsh the default shell, run `chsh -s /bin/zsh`
5. Change the prompt by editing .zshrc and adding the line `PROMPT="%B%F{blue}%~%f%b%B%F{magenta} > %f%b"`
6. Logout for changes to take effect

## Packages
This is a collection of all the packages installed in a chronological order
| package | description | usage |
| ------ | --------- | --------- |
| firefox | open source webbrowser | |
| neofetch | show info about the os and hardware | |
| git | version control system | |
| htop | task overview & manager | |
| yay | AUR manager | check this guide |
| gimp | photo manipulation suite | |
| gcolor2 | color picker utility | |
| tlp | battery improvements | check this guide for further information |
| vlc | open source media player | |
| youtube-dl | YouTube downloader | |
| deezloader | Deezer piracy utility | download from github |
| qbittorrent | torrent utiliry | |
| clementine | GUI music player | |
| cmus | console music player | |
| xarchiver | compression tool with thunar integration | |
| geany | text editor / IDE | |
| alacritty | gpu based terminal emulator | |
| bitwarden | pw manager | electron based :( install from AUR |
| lutris | wine frontend for games | install from AUR |
| ttf-hack | great monospace font | |
