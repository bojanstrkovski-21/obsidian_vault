
1. First You need to make sure you have enough space on hdd where you created the image 
2.  Next  you open the termeinal and cd into the directory where your vms are, for example default location is "/var/lib/libvirt/images" so
     "cd /var/lib/libvirt/images"
3. Next step is to run the "ls" command in the directory to see the images and choose the one you want to resize, for example .
4. Than you can run the comand "sudo qemu-img resize image.qcow2 30G" if you are directly cd in the directory or  
    "sudo qemu-img resize /var/lib/libvirt/images/image.qcow2 sizeG ( capital G not lowercase ! ) " where "size" is the size you want to add to the vm. 