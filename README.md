# hello-world
test

#!/bin/bash



[ $# -eq 1 ] || {
    echo "Usage: ${0} sdx"
    exit 1
}


cd ~/
[ -e place ] || {
    mkdir place
}


[ -e /dev/${1} ] || {
    echo "/dev/${1} does not exist"
    exit 1
}


sudo umount -f place 
sudo mount /dev/${1} place

[ -e place/e1000e-dkms_3.4.2.4s_all.deb ] || {
    echo "place/e1000e-dkms_3.4.2.4s_all.deb does not exist"
    exit 1
}
 
cp place/e1000e-dkms_3.4.2.4s_all.deb ~/


cd ~/
sudo apt-get install -y linux-headers-$(uname -r)
sudo dpkg -i e1000e-dkms_3.4.2.4s_all.deb
