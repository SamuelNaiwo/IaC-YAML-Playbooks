# YAML & Playbooks

## Create Playbook To Install Nginx in Web Machine

1. Ensure your present working directory is /etc/ansible in controller VM

2. Create a yaml file. `sudo nano install-nginx-playbook.yaml`
3. Enter the following syntax into the yaml file. Save the file once you've finished. (When indenting on YAML use two spaces instead of tab bar.)
```
# Create a playbook to install nginx in web server

# YAML file starts ---
---

# Where would you like to install nginx?
  hosts: web

# Would you like to see the logs?
  gather_facts: yes

# Do we need admin access (sudo) – Yes
  become: true

# Add the instructions (commands)
  tasks: 
    - name: Install nginx in web-server

	  apt: pkg=nginx state=present
# Ensure the status is running/active
```
4. Run the yaml file you created. `sudo ansible-playbook install-nginx-playbook.yaml`
5. To check status on nginx from web server use the following command. `sudo ansible web -a “systemctl status nginx”`