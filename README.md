# klipper-ubuntu
Klipper + Moonraker + Fluidd + Nginx +  Mjpg-streamer installer for Ubuntu targets

# Get script
You will need to have git and ansible provisioned locally. On ubuntu you can simply run the following commands to install these tools:
```shell
sudo apt-get install git ansible
```
Following that, you can download the script using the following git command:
```shell
git clone https://github.com/kevinkga/klipper-ubuntu.git
```

# Disclaimer and Caution
Do not run this script if your target host already uses Nginx. This setup will overwrite any existing nginx configuration.

In fact, it would be strongly advised to ensure that your remote target host is not running anything else as this script is in a very early stage of development. 

The developers of this script will accept no responsability in case of damage and/or loss of data due to using this script.

# Checklist
Make sure that your target host (the computer on which you want to install Klipper) meets the following requirements:
- Has Ubuntu 20.x or later installed
- Has openssh-server installed (e.g. `sudo apt-get install openssh-server`)
- You already have an admin user on the target host that has sudo privileges.

# Preparation
- Change the name and/or ip of your target installation host in the `hosts` file
- Change the name of your remote user from 'root' if necessary
```
bumblebee ansible_ssh_host=192.168.1.251 ansible_user=ubuntu
```

# Provisioning
To run the script, execute this command
```shell
ansible-playbook playbook.yml -K --ask-pass
```
You will be prompted for you remote login password. The remote user MUST have sudo access for this to work.

# Usage
Once the setup is complete you should be able to access Fluidd on your remote host via the broswer using `http://klipper:5000`. Otherwise substitute `klipper` with the DNS or IP of your remote host.

# Remote login
You can ssh to your remote host using your original OS username and password. However, if you would like to change to the klipper user then use the following command:
````shell
$ sudo su klipper
````

# Klipper configuration
Once everything is installed, please have a look at ```/home/klipper/klipper_config/printer.cfg``` and add your own printer parameters for it.

Example printers configurations can be found in ```/home/klipper/klipper/config/```

Once changed, issue the following command to restart Klipper:
```shell
sudo service klipper restart
```

Alternatively you can use the  Fluid web interface to restart Klipper

Author Information
------------------
Developed by Kevin Aubeelack (kevin@ubiclouds.com)
