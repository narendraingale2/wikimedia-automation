# wikimedia-automation

Steps to bring up this 

vagrant up
vagrant provision

# Bring up database 
ansible-playbook setup_mysql.yml --vault-password-file=~/.vault

# Bring up application
#Use db_maintain=true for first time setup 
ansible-playbook setup_mediawiki.yml --vault-password-file=~/.vault -e db_maintain=true 

# Bring up Nginx 

ansible-playbook setup_nginx.yml --vault-password-file=~/.vault

# secret file varibles:
 mysql_root_password
 
 mysql_wikimed_password
 
 ssl_crt
 
 ssl_crt_key

# Add host entry in your /etc/hosts file as below

192.168.50.100 mymediawiki.com

And you can access mediawiki 
https://mymediawiki.com/
