## manual steps

```bash
sudo adduser freddie
sudo usermod freddie -a -G pi,adm,dialout,cdrom,sudo,audio,video,plugdev,games,users,input,netdev,spi,i2c,gpio
sudo visido
# freddie ALL=(ALL) NOPASSWD: ALL

# set autologin?  https://www.raspberrypi.org/forums/viewtopic.php?t=169079#p1086575


sudo raspi-config
# enable ssh
# boot to cli
# keyboard, locale

echo $public_key to ~/.ssh/authorized_keys
ssh-keygen
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys  # local ssh without agent fwding
echo "alias ls='ls -Ahl'" >> ~/.profile


# static ip
echo "auto wlan0

iface wlan0 inet static
    address 192.168.1.25
    netmask 255.255.255.0
    gateway 192.168.1.1
" > /etc/network/interfaces.d/wlan0
sudo ifdown wlan0 && sudo ifup wlan0

sudo apt update
sudo apt upgrade
sudo apt autoremove
sudo apt install -y ansible

mkdir git
git config --global user.email "github@dustyfox.uk"
git config --global user.name "Freddie Sackur"
git config --global core.autocrlf false
git clone https://github.com/fsackur/ansible-pi
# which is where this repo comes in

cd ansible-pi
ansible-playbook playbook.yml -i hosts
```

## After installing powershell

```bash
sudo nano /etc/passwd
# set user shell to /usr/bin/powershell/pwsh
```

## VS Code settings

```json
// ~/.vscode-server/data/Machine/settings.json
{
    "terminal.integrated.shell.linux": "pwsh"
}
```
