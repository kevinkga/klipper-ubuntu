Klipper-stack
=========

Installs a full Klipper stack for 3d printers on Ubuntu linux including Klipper, Moonraker, Fluidd and mjpg-streamer

Requirements
------------
Ther target device for this role has to be a Ubuntu 21.X or later installation.

Role Variables
--------------

---
# vars file for klipper-stack
```
klipper_user: "klipper"
klipper_user_home: "/home/{{ klipper_user }}"
klipper_logs_dir: "{{ klipper_user_home }}/klipper_logs"
klipper_src_dir: "{{ klipper_user_home }}/klipper"
klipper_config_dir: "{{ klipper_user_home }}/klipper_config"
klipper_env_dir: "{{ klipper_user_home }}/klipper-env"

moonraker_log_path: "/tmp/moonraker.log"
moonraker_src_dir: "{{ klipper_user_home }}/moonraker"
moonraker_env_dir: "{{ klipper_user_home }}/moonraker-env"
moonraker_config_path: "{{ klipper_config_dir }}/moonraker.conf"
moonraker_launch_cmd: "{{ moonraker_env_dir }}/bin/python {{ moonraker_src_dir }}/moonraker/moonraker.py"
moonraker_server_ip: "{{ ansible_ssh_host }}"
moonraker_server: "{{ moonraker_server_ip }}:7125"

nginx_sites_available_path: "/etc/nginx/sites-available"
nginx_sites_enabled_path: "/etc/nginx/sites-enabled"

fluidd_assets_path: "/var/www/fluidd"
fluidd_version: "1.16.2"

webcam_server_ip: "{{ ansible_ssh_host }}"
webcam_server: "{{ moonraker_server_ip }}:8080"
```

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: klipper
      roles:
         - { role: kevinkga.klipper-stack }

License
-------
BSD

Author Information
------------------
Developed by Kevin Aubeelack (kevin@ubiclouds.com)
