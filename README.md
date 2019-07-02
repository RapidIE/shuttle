# shuttle
Automated deployment of Spacewalk with local PostgreSQL database via Ansible

## Requirements
- Ansible
- RHEL7 or CentOS7 OS installed

1. Clone this repo
```
 git clone https://github.com/RapidIE/shuttle.git
 ```
 
 2. Modify the hosts.ini file to suit your situation. If you want to run locally on the server you wish to install Spacewalk on, setup the file like below. If you are running it remotely, ensure you have root SSH keys setup.
 
 ```
 [spacewalk]
 localhost
 ```
 
 3. Modify the answers file found in the files directory. Update the cnames, email, password parameters, City, State, etc. Below is an example configuration
 ```
 admin-email = root@localhost
ssl-set-cnames = spacewalk,spacewalk.home.local
ssl-set-org = Spacewalk Org
ssl-set-org-unit = spacewalk
ssl-set-city = Austin
ssl-set-state = Texas
ssl-set-country = US
ssl-password = changeme!!
ssl-set-email = root@localhost
ssl-config-sslvhost = Y
db-backend=postgresql
db-name=spaceschema
db-user=spaceuser
db-password=changeme!!
db-host=localhost
db-port=5432
enable-tftp=Y
```

4. Run the playbook
```
 ansible-playbook -i hosts.ini spacewalk-server.yaml
 ```
 
 That's it! You can now access the Spacewalk GUI by pointing your browser to the DNS name and setup your first user.
 Example:
 https://spacewalk.home.local
