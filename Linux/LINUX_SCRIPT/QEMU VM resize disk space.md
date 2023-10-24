
1. First You need to make sure you have  open termeinal and cd into the directory where your vms are, for example default location is "/var/lib/libvirt/images"
2. Next step is to ls the directory to see the images so yopu cen choose the one you want to resize.
3. Than you can run the comand "sudo qemu-img resize image.qcow2 30G" if you are directly cd in the directory or  
    "sudo qemu-img resize /var/lib/libvirt/images/image.qcow2 sizeG ( capital G not lowercase ! ) " where "size" is the size you want to add to the vm. 