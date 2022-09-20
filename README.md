# rh-sat-create-hosts-playbook
Creates pysical and virtual hosts in Red Hat Satellite

## Desscription
This is an Ansible Playbook which creates new hosts on a Red Hat Satellite server. You can deploy virtual and physical servers. The password is stored in an Ansible Vault file. Alternatively you can omit the credentials and you will get prompted for username and/or password. Depending on the usecase this can make sense.

## Usage
1. First of all review the vars.yml to fit your environment. If you like to get promted for the username when running the playbook, just commend out the line "sat_user". 

2. Change the password for the vault file "passwd.yml" by issuing `ansible-vault rekey passwd.yml`. The default password is "changeme.

3. Edit the "passwd.yml" with `ansible-vault edit passwd.yml`. Set the actual password for the user defined in the vars.yml. Optionally you can get rid of the vault file by comment out the line "- passwd.yml" in the Playbook "create_host.yml". In that case, also comment the line "ask_vault_pass = True" in the ansible.cfg file. If you do so, you will get promted for the password when running the Playbook. Echo is turned off.

4. You can overwrite the variables defined in the vars.yml file by using the parameter "--extra-vars". I.e. `ansible-playbook create_host.yml --extra-vars="ip=10.10.10.11"

## Requirements
You need to have the package "ansible-collection-redhat-satellite" installed. 

## Contributions
Feel free to send my a merge request on Github. Contributions are very welcome.
