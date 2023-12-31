```
sudo apt install zfsutils-linux
sudo apt install nfs-kernel-server

sudo zpool create -o ashift=12 -f nas raidz2 ata-WDC_WD10EFRX-68FYTN0_WD-WCC4J0SEF254 ata-WDC_WD10EFRX-68FYTN0_WD-WCC4J0SEFN9A ata-WDC_WD10EFRX-68FYTN0_WD-WCC4J0TDU34X ata-WDC_WD10EFRX-68FYTN0_WD-WCC4J0TDUPT3 ata-WDC_WD10EFRX-68FYTN0_WD-WCC4J7VF4NUS
sudo zfs set atime=off nas
sudo zfs set compression=lz4 nas

sudo zfs create nas/Media
sudo zfs set sharenfs=on nas/Media
sudo zfs set sharenfs="rw=@192.168.50.0/24" nas/Media
sudo chmod 777 /nas/Media

sudo zfs create nas/syncthing
sudo zfs set sharenfs=on nas/syncthing
sudo zfs set sharenfs="rw=@192.168.50.0/24" nas/syncthing
sudo chmod 777 /nas/syncthing

sudo zfs create nas/backup
sudo zfs set sharenfs=on nas/backup
sudo zfs set sharenfs="rw=@192.168.50.0/24" nas/backup
sudo chmod 777 /nas/backup

sudo zfs create nas/music
sudo zfs set sharenfs=on nas/music
sudo zfs set sharenfs="rw=@192.168.50.0/24" nas/music
sudo chmod 777 /nas/music

sudo zfs create nas/immich
sudo zfs set sharenfs=on nas/immich
sudo zfs set sharenfs="rw=@192.168.50.0/24" nas/immich
sudo chmod 777 /nas/immich
```

```
pip3 install ansible
ansible-galaxy install -r requirements.yml
```

```
ansible-playbook -i inventory main.yml -K
```

```
ansible all -i inventory -m command -a 'docker version'
ansible all -i inventory -m command -a 'docker ps'
ansible all -i inventory -m command -a 'docker-compose version'
```

## cloudflared
```bash
wget -q https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb && sudo dpkg -i cloudflared-linux-amd64.deb

cloudflared tunnel login

cloudflared tunnel create homelab
```
