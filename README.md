# Ansible Playbooks for Raspberry Pi setup

### Step 1:

Flash an SD card with Raspbian image.

Make sure you [add the `ssh` file](https://www.raspberrypi.org/forums/viewtopic.php?t=129727) to the boot image.

Insert the card and boot the pi

### Step 2:

Install ansible and passlib:

    $ pip install ansible
    $ pip install passlib

### Step 3:

Find the IP address of the pi on your network.

Copy SSH keys over:

    $ ssh-copy-id -i ~/.ssh/id_rsa.pub pi@<IP_ADDRESS_OF_PI>

### Step 4: Configure the host and group variables

Add an entry for each pi in the `hosts` file.

Update variables for wifi in `group_vars/defaultdevices`

Update individual host files in `host_files/<HOSTNAMES>`

### Step 5:

Run Ansible:

    $ ansible-playbook -v -i hosts playbooks/new-default.yml

## Editing encrypted files

    $ ansible-vault edit path/to/file --vault-id .ansible-vault-password
