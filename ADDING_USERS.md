adduser <username>
cd /home/<username>
mkdir .ssh
touch .ssh/authorized_keys
nano authorized_keys
# add .ssh key inside file

visudo
<username> ALL=(ALL) NOPASSWD: ALL
