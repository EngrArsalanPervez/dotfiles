# Archlinux Bootstrap

## OS Installation

### Internet

```bash
# Wired - DHCP
ping www.google.com

# Wifi
iwctl
device list
station wlan0 connect WIFI_NAME
passphrase
exit
ping 8.8.8.8
ping www.google.com
```

### Update Installer

```bash
pacman -Sy
pacman -S archlinux-keyring archinstall
```

### Wipe HDD

```bash
lsblk
gdisk /dev/sda
x
z
```

### Archinstall

```bash
archinstall # Keep everything default
# Drop to chroot for Post Installation
pacman -S fastfetch firefox haruna libreoffice-fresh gcc make cmake git nano vim htop power-profiles-daemon flatpak rust wget curl perl
exit
shutdown now
```

## First-Boot

## visudo

```bash
sudo EDITOR=nano visudo
# Add at the end
eup    ALL=(ALL) NOPASSWD:ALL
```

## Update / Upgrade

```bash
sudo pacman -Syu --noconfirm #Update/Upgrade
# -S → sync/install
# -y → refresh package database
# -u → upgrade all packages
sudo pacman -S --needed base-devel --noconfirm
```

## yay

```bash
cd /tmp
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
yay --version
yay -Syu
```

## Basics

```bash
sudo pacman -Syu --noconfirm #Update/Upgrade
sudo pacman -S --needed tree openssh tmux net-tools inetutils iputils netcat hping nmap sshfs git curl wget lazygit sshpass htop btop fastfetch screen libxml2 hyperscan traceroute vlc python python-pip python-virtualenv python-pyelftools python-scapy wireshark-qt tcpdump ethtool iperf3 partitionmanager ntfs-3g --noconfirm
# Enable SSH
sudo systemctl enable --now sshd
yay -S ifstat
```

## C

```bash
# C Programming
sudo pacman -Syu --noconfirm #Update/Upgrade
sudo pacman -S ctags cscope global
sudo pacman -S valgrind strace ltrace perf
sudo pacman -S man-db man-pages tldr
sudo pacman -S cppcheck clang-analyzer
sudo pacman -S linux-headers bpf bpftrace
sudo pacman -S tcpdump wireshark-qt iperf3 nmap traceroute
sudo pacman -S git lazygit
sudo pacman -S ripgrep fd bat eza fzf
sudo pacman -S numactl hwloc
sudo pacman -S --needed ctags base-devel cmake openssl zlib elfutils libpcap numactl libevent libbsd man-pages ncurses flex bison bc clang llvm lldb lld clang-tools-extra gdb meson ninja pkgconf valgrind bear ccache doxygen graphviz cppcheck pahole perf --noconfirm
yay -S dwarves ack
```

## DPDK

```bash
sudo pacman -Syu --noconfirm #Update/Upgrade
sudo pacman -S --needed pkgconf base-devel meson ninja numactl dtc libbpf libxdp libarchive jansson --noconfirm
```

## Lazyvim Pre-Requisite

```bash
sudo pacman -Syu --noconfirm #Update/Upgrade
sudo pacman -S --needed python-pynvim --noconfirm
sudo pacman -S --needed nodejs npm --noconfirm
sudo pacman -S --needed xclip ripgrep fzf fd luarocks imagemagick texlive-core --noconfirm
sudo npm install -g tree-sitter-cli @mermaid-js/mermaid-cli neovim
```

## Go

```bash
sudo pacman -Syu --noconfirm #Update/Upgrade
sudo pacman -S --needed go --noconfirm
```

## NeoVim Latest

```bash
sudo pacman -Syu --noconfirm #Update/Upgrade
sudo pacman -S --needed neovim --noconfirm
```

## Docker

```bash
sudo pacman -Rs docker docker-compose containerd runc
sudo pacman -Syu --noconfirm #Update/Upgrade
sudo pacman -S --needed docker docker-compose docker-buildx containerd --noconfirm
sudo systemctl enable --now docker
sudo groupadd -f docker
sudo usermod -aG docker $USER
sudo docker run hello-world
```

## Tmux

```bash
sudo pacman -S --needed --noconfirm alacritty tmux
# Setup config from: https://github.com/EngrArsalanPervez/tmux
```

## yazi

```bash
sudo pacman -S --needed ffmpeg p7zip jq poppler fd ripgrep fzf zoxide imagemagick xclip wl-clipboard --noconfirm
sudo pacman -Syu yazi --noconfirm
yazi --version
echo "alias yy='yazi'" >> ~/.bashrc
source ~/.bashrc
yy
rm -rf ~/.cache/yay/*
```

## Default Editor

```bash
echo 'export EDITOR="nvim"' >> ~/.bashrc
echo 'export VISUAL="nvim"' >> ~/.bashrc
source ~/.bashrc
echo $EDITOR   # outputs: nvim
echo $VISUAL   # outputs: nvim
```
