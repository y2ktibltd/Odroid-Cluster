# Odroid-Cluster

dont forget to generate ssh keys and upload them to your cluster nodes before you start using dsh. 
you will also want to change the individual nodes to allow running commands as root w/o password confirm.

#sudo visudo

uncomment out the line...

## Same thing without a password
%wheel ALL=(ALL) NOPASSWD: ALL
