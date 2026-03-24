# Ubuntu

## visudo

```bash
sudo visudo
# Add at the end
network    ALL=(ALL) NOPASSWD:ALL
```

## Update

```bash
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade
sudo apt install build-essential
```

## Basics

```bash
sudo apt install -y openssh-server openssh-client tmux tshark net-tools telnet hping3 nmap arping sshfs git curl wget lazygit sshpass
sudo apt install -y htop btop fastfetch wireshark screen libcurl4-openssl-dev libxml2-dev
sudo apt install -y netcat-traditional traceroute
sudo apt install -y vlc ifstat
sudo apt install -y python3-venv python3-pip python3-pyelftools python3-full python3-dev
sudo apt install -y synaptic
sudo apt install -y libhyperscan-dev
sudo apt install -y librust-aho-corasick+std-dev
sudo apt install -y python3-scapy

```

## C

```bash
# C Programming
sudo apt install -y universal-ctags build-essential cmake ack
sudo apt install -y libssl-dev zlib1g-dev libelf-dev libpcap-dev libnuma-dev libevent-dev libbsd-dev
sudo apt install -y manpages-dev manpages-posix-dev
sudo apt install -y libncurses-dev flex bison dwarves bc
sudo apt install -y clang clangd clang-format clang-tidy gdb lldb cmake meson ninja-build pkg-config gdb lldb valgrind bear ccache doxygen graphviz clang-tools cppcheck
```

## DPDK

```bash
sudo apt install -y pkg-config build-essential meson ninja-build libnuma-dev
sudo apt install -y libfdt-dev libbpf-dev libxdp-dev libarchive-dev libjansson-dev
```

## Lazyvim Pre-Requisite

```bash
sudo apt install -y python3-pynvim -y
sudo apt install -y npm nodejs
sudo apt install -y xclip ripgrep fzf ripgrep fd-find luarocks imagemagick texlive-latex-base
sudo npm install -y -g node tree-sitter-cli @mermaid-js/mermaid-cli neovim
sudo apt install -y python3-pynvim
sudo ln -s /usr/bin/fdfind /usr/bin/fd
fd
```

## Go

```bash
cd Downloads
wget https://go.dev/dl/go1.25.6.linux-amd64.tar.gz
sudo -s
rm -rf /usr/local/go && tar -C /usr/local -xzf go1.25.6.linux-amd64.tar.gz

# with and with sudo
mkdir -p ~/go/{bin,pkg,src}
echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc
echo 'export GOPATH=$HOME/go' >> ~/.bashrc
echo 'export GOBIN=$HOME/go/bin' >> ~/.bashrc
echo 'export PATH=$PATH:$GOBIN' >> ~/.bashrc
source ~/.bashrc
```

## NeoVim Latest

```bash
cd Downloads
wget https://github.com/neovim/neovim/releases/download/v0.11.5/nvim-linux-x86_64.appimage
sudo chmod 777 nvim-linux-x86_64.appimage
sudo cp nvim-linux-x86_64.appimage /usr/bin/nvim
```

## Docker

```bash
sudo apt remove $(dpkg --get-selections docker.io docker-compose docker-compose-v2 docker-doc podman-docker containerd runc | cut -f1)

```

```bash
# Add Docker's official GPG key:
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Signed-By: /etc/apt/keyrings/docker.asc
EOF

sudo apt update
```

```bash
 sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
 sudo systemctl status docker
 sudo docker run hello-world
 sudo groupadd docker
 sudo usermod -aG docker $USER
```

## Tmux

```bash
# Setup config from: https://github.com/EngrArsalanPervez/tmux
```

## Yazi

```bash
# Setup config from: https://github.com/EngrArsalanPervez/yazi_kitty
```

## Grub: IOMMU / Hugepages (256GB on each socket)

```bash
sudo nano /etc/default/grub
  GRUB_CMDLINE_LINUX_DEFAULT="default_hugepagesz=1G hugepagesz=1G hugepages=512 intel_iommu=on iommu=pt"
sudo update-grub
sudo reboot
```

## X710 Firmware Update

```bash
URL: https://www.intel.com/content/www/us/en/download/18190/non-volatile-memory-nvm-update-utility-for-intel-ethernet-network-adapter-700-series.html

mkdir bootstrap/x710/
cd x710/
download 700Series_NVMUpdatePackage_v9_56.zip
unzip 700Series_NVMUpdatePackage_v9_56.zip
tar -xzf 700Series_NVMUpdatePackage_v9_56_Linux.tar.gz
cd 700Series/Linux_x64
sudo ./nvmupdate64e -l
#Tool execution completed with the following status: All operations completed successfully.

# Verify
ethtool -i ens785f0np0
# firmware-version: 9.56 0x80010122 1.1747.0

reboot
```

## DPDK

```bash
# Install dpdk
git clone git://dpdk.org/dpdk-kmods

sudo mkdir -p /dev/hugepages
sudo mount -t hugetlbfs nodev /dev/hugepages
```

## Git ssh

```bash
# Copy paste id_ed25519* into ~/.ssh

git config --global credential.helper store
git config --global user.email "usman.pervez@git.com"
git config --global user.name "usman.pervez"

git token:
glpat-olmmJhM9dbCzB0oE6Z7naW86MQp1OjcH.01.0w07oaeep

```

## /etc/hosts

```bash
192.168.0.1 example.com
```
