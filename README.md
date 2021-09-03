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

# Discalimer and Caution
Do not run this script if your target host already uses Nginx. This setup will overwrite any existing nginx configuration.

In fact, it would be strongly advised to ensure that your remote target host is not running anything else as this script is in a very early stage of development. 

The developers of this script will accept no responsability in case of damage and/or loss of data due to using this script.

# Preparation
- Change the name and/or ip of your target installation host in the `hosts` file
- Change the name of your remote user from 'root' if necessary
```
klipper ansible_ssh_host=192.168.1.146 ansible_user=root
```

# Provisioning
To run the script, execute this command
```shell
ansible-playbook playbook.yml --limit klipper -K
```
You will be prompted for you remote login password. The remote user MUST have sudo access for this to work.

# Usage
Once the setup is complete you should be able to access Fluidd on your remote host via the broswer using `http://klipper:5000`. Otherwise substitute `klipper` with the DNS or IP of your remote host.

# Remote login
You can ssh to your remote host using your original OS username and password. However, if you would like to change to the klipper user then use the following command:
````shell
$ sudo su klipper
````
