Create a slice of host disk for k8s local storage

*Create local volume
  `mkdir /mnt/k8s`
  `dd if=/dev/zero of=/opt/k8s.local bs=1 count=1 seek=75G`
  `mkfs.ext4 /opt/k8s.local`
  `vim /etc/fstab`

*Add volume to mount
   `/opt/k8s.local  /mnt/k8s        ext4    defaults,noatime 0 1`

*On the Controller
  `git clone https://github.com/kubernetes-sigs/sig-storage-local-static-provisioner.git`
  `helm install -f helm/examples/baremetal.yaml local-stroage-provisioner --namespace default ./helm/provisioner`
