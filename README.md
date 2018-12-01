# Ansible Playbooks for Raspberry Pi setup

### Step 1:

Flash an SD card with Raspbian image.

Make sure you [add the `ssh` file](https://www.raspberrypi.org/forums/viewtopic.php?t=129727) to the boot image.

Insert the card and boot the pi

### Step 2:

Install ansible and passlib on a host machine that will then configure the raspberry pi.

    $ pip install ansible
    $ pip install passlib

### Step 3:

Connect the raspi to an ethernet port.

Log into the router and write down the IP address of the pi.

### Step 4: Configure the host and group variables

Add an entry for each pi in the `hosts` file.

Update variables for wifi in `group_vars/defaultdevices`

Update individual host files in `host_files/<HOSTNAMES>`

### Step 5:

Run Ansible:

    $ ansible-playbook -v -i hosts playbooks/new-default.yml --vault-id .ansible-vault-password --ask-pass

Note that the first time you run this, you will want to include the `--ask-pass` flag because the SSH key hasn't been copied over to the pi.

## Editing encrypted files

    $ ansible-vault edit path/to/file --vault-id .ansible-vault-password
