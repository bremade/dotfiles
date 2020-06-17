# My Dotfiles

These are the dotfiles deployed by [Jan Bremauer](https://bremauer.cc)

- Very useful scripts are in `~/.local/bin/`
- Settings for:
	- zsh (shell)
	- i3 (window manager)
	- i3Status (status bar)
	- other stuff like ..., etc.

## Install the dotfiles

Clone the repo files directly to your home directory.
```
git clone git@github.com:sirarzelot/dotfiles.git
```

## Set up Linux

Install needed packages
```
sudo apt install git i3 rofi zsh fonts-font-awesome grub-customizer
```

Clone dotfiles

Set up Zsh
```
Set background to #282b34
```

Install fonts
```
git clone https://github.com/powerline/fonts.git --depth=1
cd fonts
./install.sh
cd ..
rm -rf fonts
```

Install oh-my-zsh
```
sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Install zsh-autosuggestions
```
git clone https://github.com/zsh-users/zsh-autosuggestions.git $ZSH_CUSTOM/plugins/zsh-autosuggestions
```

Install zsh-syntax-highlighting
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
```

Install spaceship theme
```
git clone https://github.com/denysdovhan/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt"
ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme"
```
Install i3Blocks
```
git clone https://github.com/vivien/i3blocks
cd i3blocks
./autogen.sh
./configure
make
make install
cd ..
rm -rf i3blocks
```

Install Fira Code
```
#!/usr/bin/env bash

fonts_dir="${HOME}/.local/share/fonts"
if [ ! -d "${fonts_dir}" ]; then
    echo "mkdir -p $fonts_dir"
    mkdir -p "${fonts_dir}"
else
    echo "Found fonts dir $fonts_dir"
fi

for type in Bold Light Medium Regular Retina; do
    file_path="${HOME}/.local/share/fonts/FiraCode-${type}.ttf"
    file_url="https://github.com/tonsky/FiraCode/blob/master/distr/ttf/FiraCode-${type}.ttf?raw=true"
    if [ ! -e "${file_path}" ]; then
        echo "wget -O $file_path $file_url"
        wget -O "${file_path}" "${file_url}"
    else
	echo "Found existing file $file_path"
    fi;
done

echo "fc-cache -f"
fc-cache -f
```

Set up grub
```
git clone git@github.com:vinceliuice/grub2-themes.git
cd grub2-themes
// Laptop
sudo bash ./install.sh -t
// Desktop
sudo bash ./install.sh -t -2
cd ..
rm -rf grub2-themes
```
