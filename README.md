# Cisco Secure Endpoint Ansible Playbooks
This is a collection of ansible playbooks I used for maintaining and setting up my homelab while supporting Secure Endpoint. These are not a complete list of playbooks, roles, or tasks. These are intended to assist administrators in installing, uninstalling, and collecting diagnostic data where needed. In the end, they are relatively simple.

## Disclaimer
The source code, opinions, expressions, and other work product included in this repository are not endorsed, supported, and otherwise representative of any of my current or previous employers unless otherwise stated. This work is provided as is, with no warrantees, gurantees, or support. By using this product, you are doing so at your own risk.


# Installing Cisco Secure Endpoint (Ubuntu/Debian)
```bash
ansible-playbook -i <my_inventory_file> tasks/02-apt-based-install-cisco-amp.yml
```
The playbook will ask you for a Download URL, which can be gathered from the Secure Endpoint console under "Management" --> "Download Connectors"

# Uninstalling Cisco Secure Endpoint (Ubuntu/Debian)
```bash
ansible-playbook -i <my_inventory_file> tasks/00-apt-based-uninstall.yml
```
This will run a number of tasks, first removing the connector via the package manager, purging all remnants, ensuring all services are disabled and deleted, and restarting the systemd daemon.

# Gather Diagnostic Bundle (Ubuntu/Debian)
```bash
ansible-playbook -i <my_inventory_file> tasks/01-apt-based-diagnostic-bundle.yml
```
When running this task, you will be asked for a location on your local machine to download the diagnostic bundle to. This is '~/Downloads' by default. In addition, you will be asked for how long you want to run the connector is debug log mode. This is in secods, and is set to '600' by default.

This playbook uses python3-pexpect to make this as seamless as possible, as ampcli and other executables expect an interative user when setting log level modes.

# Notes
I probably won't be adding anything else here, as I will no longer be supporting Cisco Secure Endpoint moving forward, but I may make some minor additions like including some playbooks/tasks for Enterprise Linux distros that use yum/dnf as their package manager.