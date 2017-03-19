# Ansible Playbook for Django using boto3 SDK
Ansible script deploying Django project which use Amazon Web Services
 * based on [technivore](https://github.com/technivore/ansible-django)
 
## Using Steps
1. Create boto3 config/credential files as described [here](http://boto3.readthedocs.io/en/latest/guide/quickstart.html#configuration)
2. Define config/credential files in **vars.yml**.  
```
aws_config: ~/.aws/config  
aws_credentials: ~/.aws/credentials
```  
3. Define git repo and ssh key in **vars.yml**. 
```
project_repo: git@github.com:meletakis/aws_stack.git  
ssh_private_key: ~/.ssh/id_rsa
```
3. Define host, user, pass for remote server (ssh connection) in **hosts**. 
```
[servers]  
xxx.xxx.xxx.xxx ansible_connection=ssh  ansible_user=MYUSER ansible_password=MYUSERPASS
```
4. Define Django info in **vars.yml**
```
project_name: webapp
wsgi_module: webapp.wsgi
static_root: "{{ install_root }}/{{ project_name }}/static"
```
5. Run ansible playbook
```
ansible-playbook -i hosts provision.yml --ask-sudo-pass
```
