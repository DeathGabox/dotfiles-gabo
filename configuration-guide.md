> Note: This is a forever work in progress

- [x] Read The Fabulous Manual ([RTFM](https://es.wikipedia.org/wiki/RTFM)) always, like [Archwiki](https://wiki.archlinux.org/) or Self-doc written by project, this is considered out of date by design

# Configuration
## Firefox Config 

- [SimpleFox CSS Repo](https://github.com/migueravila/SimpleFox)

> Write in searchbar `about:config` and turn "True" to next params :
```
- toolkit.legacyUserProfileCustomizations.stylesheets
- layers.acceleration.force-enabled
- gfx.webrender.all
- svg.context-properties.content.enabled
```

> Note1: $Firefox-Channel is the firefox Channel you selected, examples `Nightly` `Beta` `Developer` `Normal` `ESR`
> 
> Note2: Mozilla create weird names to the $Firefox-Default-Folder, for me, `Firefox -> u0kchxzv.default` `Firefox Developer Edition -> idknp77f.dev-edition-default` `Firefox-ESR -> rycwnmek.default-release`
```
cd ~/.mozilla/$Firefox-Channel/$Firefox-Default/
mkdir chrome
mv ~/Documents/git/dotfiles-gabo/.mozilla/$CSS-Folder/* chrome/
```

### Fish Config
NOTE: You need to redo all step in root mode to have fisher working well

<details>
 <summary><b>Install Fisher</b></summary>
 <br>

```
curl -sL https://raw.githubusercontent.com/jorgebucaran/fisher/main/functions/fisher.fish | source && fisher install jorgebucaran/fisher
```

> Fisher Plugins
> Install [Tide](https://github.com/IlanCosman/tide)
```
fisher install IlanCosman/tide@v6
```

> Install [Done](https://github.com/franciscolourenco/done)
```
fisher install franciscolourenco/done
```

> Install [Alias Assisntant](https://github.com/paysonwallach/fish-you-should-use/)
```
fisher install paysonwallach/fish-you-should-use
```

> Install [Alias Ideas](https://github.com/gazorby/fish-abbreviation-tips)
```
fisher install gazorby/fish-abbreviation-tips
```

> Let Fish Shell Default
```
chsh -s /bin/fish
```

> NOTE: Config File Default are
```
~/.config/fish/config.fish
~/.config/fish/conf.d/
```

</details>

> Move .config with your configurations:
> NOTE: To work, you need [Nerd Fonts](https://www.nerdfonts.com/), like HackNerdFont or JetBrains
- Kitty
- Fastfetch
- Hyprland
- qt5ct
- qt6ct
```
mv ~/Documents/git/dotfiles-gabo/.config ~/.config
```

### THEME

My Favs <3
- Theme GTK [Nordic](https://github.com/EliverLara/Nordic)
- Theme QT [Catppucin](https://github.com/catppuccin/qt5ct)
- Icons [Papirus Icon Theme](https://archlinux.org/packages/community/any/papirus-icon-theme/)
- Mouse [Volante Cursors](https://github.com/varlesh/volantes-cursors)

```
cd /home/$USER/Documentos/github
git clone https://github.com/EliverLara/Nordic.git
sudo mv Nordic/ /usr/share/themes
```

> Cursors
```
cd /home/$USER/Documentos/github
git clone https://github.com/varlesh/volantes-cursors.git
cd volantes-cursors
make build
sudo make install
```

https://github.com/catppuccin/qt5ct

> QT
> NOTE: add `QT_QPA_PLATFORMTHEME=qt5ct` to your env file and reboot

<details>
 <summary><b>Configure qt6ct user & root</b></summary>
 <br>

User Files
```
- Configuration path: "/home/deathgabox/.config/qt6ct"
- Shared QSS paths:"/usr/share/qt6ct/qss")
- Shared color scheme paths: "/usr/share/qt6ct/colors")
```

Root Files
```
- Configuration path: "/root/.config/qt6ct"
- Shared QSS paths:"/usr/share/qt6ct/qss")
- Shared color scheme paths:"/usr/share/qt6ct/colors")
```

Colors
```
Catppuccin-Frappe.conf      (Light Mode)
Catppuccin-Latte.conf       (Dark Mode)
Catppuccin-Macchiato.conf   (Darker Mode)
Catppuccin-Mocha.conf       (Darkest Mode)
```

</details>

## TTY
> Clone and Copy Files
```
cd ~/Documents/git
https://github.com/catppuccin/tty.git && cd tty
chmod a+x *.sh
./generate.sh macchiato
```
> Edit `/etc/default/grub` and append the stdin of sh script to `GRUB_CMDLINE_LINUX`


## Grub2
> Clone and Copy Files
```
cd /home/$USER/Documentos/git
git clone https://github.com/catppuccin/grub.git && cd grub
sudo cp -r src/* /usr/share/grub/themes/
```
> Edit `/etc/default/grub` and add `GRUB_THEME="/usr/share/grub/themes/catppuccin-macchiato-grub-theme/theme.txt"`
> Next run:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

# Extra-Config
## Thunar Macros
> 
> NOTE: Modify $Printer to your printer

`exec kitty --working-directory %f`
`lp -d $Printer -o fit-to-page -o media=letter %f`

## SDDM

> Theme [Aur](https://aur.archlinux.org/packages/sddm-theme-tokyo-night)
>
> Installation
```
cat ~/Documents/git/dotfiles-gabo/.package-backup/theme.conf > /usr/share/sddm/themes/tokyo-night-sddm/theme.conf
```
