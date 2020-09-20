# Working Notes

## Learn how to create a HA Kubernetes cluster on Raspberry Pis.

[Automated HA Kubernetes deployment on Raspberry Pis](https://itnext.io/automated-ha-kubernetes-deployment-on-raspberry-pis-408f38cd836c)


# [Downloads the Flash tool](https://github.com/raspbernetes/k8s-cluster-installation/tree/master/setup#downloads-the-flash-tool)
```aidl
sudo curl -L "https://github.com/hypriot/flash/releases/download/2.5.0/flash" -o /usr/local/bin/flash
sudo chmod +x /usr/local/bin/flash
```
[Cloud-Init Documentation](https://cloudinit.readthedocs.io/en/0.7.9/)

#SSH

```aidl
ssh -i ~/.ssh/id_rsa  pi@k8s-worker/master-0N
```