# XFCE Setup & Customizing
This guide is ment as a collection of many different changes done to the XFCE desktop environment, be it fixes for issues or quality of life changes.

## Changelog
| Date | Comment |
| ------ | ------ |
| 2020/05/01 | created the document |

## to do
- [ ] nothing

## Fixes
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

## Important packages
### TLP - battery improvements for laptops
1. install the following packages `pacman -S tlp tlp-rdw tp_smapi acpi_call`
2. enable services: `systemctl enable tlp.service`
3. enable services: `systemctl enable NetworkManager-dispatcher.service`
4. mask the following services: `systemctl mask systemd-rfkill.service`, `systemctl mask systemd-rfkill.socket`

### yay - AUR manager
1. Download from git: `git clone https://aur.archlinux.org/yay.git`
2. cd into the directory: `cd yay`
3. Make: `makepkg -si`

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
