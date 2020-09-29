# Working Notes

## Learn how to create a HA Kubernetes cluster on Raspberry Pis.

[Automated HA Kubernetes deployment on Raspberry Pis](https://itnext.io/automated-ha-kubernetes-deployment-on-raspberry-pis-408f38cd836c)


# [Downloads the Flash tool](https://github.com/raspbernetes/k8s-cluster-installation/tree/master/setup#downloads-the-flash-tool)
```aidl
sudo curl -L "https://github.com/hypriot/flash/releases/download/2.5.0/flash" -o /usr/local/bin/flash
sudo chmod +x /usr/local/bin/flash
```
[Cloud-Init Documentation](https://cloudinit.readthedocs.io/en/20.3/topics/examples.html)

#SSH

```aidl
ssh -i ~/.ssh/id_rsa  pi@k8s-worker/master-0N
```

# Raspberry Pi Monitoring

```aidl
sudo apt-get update && sudo apt-get install htop -y
```

# Setup Intel node

## UID:
dbuddenbaum

## hostname
k8s-i7wrker-01

# Networking

## Install SSH server and client metapackage using the apt command:
$ sudo apt install ssh
##Enable and start SSH server daemon:
$ sudo systemctl enable --now ssh
##Check SSH server status:
$ sudo systemctl status ssh

## path: /etc/netplan/10-cloud-init.yaml

```aidl
network:
  version: 2
  ethernets:
    eth0:
        dhcp4: false
        addresses: [192.168.2.55/24]
        gateway4: 192.168.2.253
        nameservers:
            addresses: [8.8.8.8, 4.4.4.4]
```

## Apply networking

sudo netplan apply

## Disable Swap

* Open fstab file, type sudo gedit /etc/fstab in terminal.

```
File's contents would look like this:

proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
#/dev/sda10 /media/ASD  vfat    defaults    0   0
#/dev/sda1  /media/98   vfat    defaults    0   0

```

* Just add hash (#) to the beginning of the swap partition line, so the line looks as:

```
#/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
```

* Reboot your PC


## NETWORK ISSUES

### Set /proc/sys/net/bridge/bridge-nf-call-iptables to 1 by running


* sudo vim /etc/sysctl.d/99-kubernetes-cri.conf
```aidl
net.bridge.bridge-nf-call-iptables=1
net.bridge.bridge-nf-call-ip6tables=1
net.bridge.bridge-nf-call-arptables=1
net.ipv4.ip_forward=1
```

* sudo modprobe br_netfilter



