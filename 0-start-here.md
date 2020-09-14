# Universal changes
Covering the common service initialization managers (more to come), and generic/base distros. (Open)Suse and BSD Linux if someone has already done a writeup. 
These are generic things that need to be modified, and where to find the files that need changing. When I get a working install "blob" with networking for Void Linux on ARM (Raspberry Pi) I will add that info too, but its should be similar to Alpine.

# Debian 10 Buster
 - Ubuntu 20.04 LTS Focal Fossa
 - Linux Mint 20 Ulyana
 - Raspbian 10 Buster
 - Raspberry Pi OS 4.19

# Alpine Linux
 - docker images
 - `apk` package manager
 - basis for many small distros (400-500 Mb, not Gb)
  
# /etc/logrotate.conf
 - defaults: weekly, rotate 4, create, include /etc/logrotate.d/*

# systemd-analyze blame
 - **apt** - `sudo systemctl stop apt-daily-upgrade apt-daily ; sudo systemctl disable apt-daily-upgrade apt-daily`
 - **apt-timer** - `sudo systemctl stop apt-daily-upgrade.timer apt-daily.timer ; sudo systemctl disable apt-daily-upgrade.timer apt-daily.timer`
 - **man** - `sudo systemctl stop man-db.timer ; sudo systemctl disable man-db.timer`
 - **nfs** - `sudo systemctl stop nfs* ; sudo systemctl disable nfsd.service nfs-ganesha.service nfs-ganesha-lock.service nfs-idmapd.service nfs-kernel-server.service nfs-mountd.service nfs-server.service`
 - **samba** - `sudo systemctl stop smbd.service ; sudo systemctl disable smbd.service`

# systemd-analyze critical-chain
 - for boot services that have to wait on others before they can complete

