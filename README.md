# Ansible Webmin Installer

[Ansible](http://www.ansible.com/home) role to:
- Install Webmin
- Setup firewall rules to open webmin port (ufw only for now)

## Supported platforms

- Ubuntu 18.04 LTS (Bionic)
- Ubuntu 20.04 LTS (Focal Fossa)
- Debian 9 (Stretch)
- Debian 10 (Buster)

## Quick start

To use this as a role clone this repo inside the *role/* folder in your Ansible project.

The latest webmin version from the APT repository will be installed and 
if ufw configuration is selected it will open port 10000 to the IPs defined in configuration 

### Example playbook

```yml
---

# webmin.yml

- hosts: "all"
  become: true
  roles:
    - role: "webmin"
```

Usage: `ansible-playbook webmin.yml`

## Default role variables

### Installing webmin

You can use the defaults for regular install. Change the following vars only if necessary.

You can add more packages to be installed in apt_dependencies:

```yml
webmin_apt_dependencies:
    - apt-transport-https
```

In case of necessity you can switch the apt key and repo urls:
```yml
webmin_apt_key_url: https://download.webmin.com/jcameron-key.asc
webmin_apt_repo_url: https://download.webmin.com/download/repository
```

### Firewall

Sets firewall rules - only ufw is supported for now

To open port 10000 set to true|yes (default is false):
```yml
webmin_ufw: yes
```

Select the IP addresses/ranges to which port 10000 should be open. use 0.0.0.0/0 to open to all:
```yml
webmin_fw_from_ips: 
    - '192.168.0.0/24'
```

## License

MIT