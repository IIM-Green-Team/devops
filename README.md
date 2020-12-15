# Green Team's devops repo

* Front : [zerodechet.io](http://zerodechet.io/)
* API : [api.zerodechet.io](http://api.zerodechet.io/)

## Contributors
<!-- [![punkte](https://github.com/Punkte.png?size=50)](https://github.com/Punkte)
[![Etienne Mela](https://github.com/EtienneMela.png?size=50)](https://github.com/EtienneMela)
[![Adrien BANNWARTH](https://github.com/Adrienbannwarth.png?size=50)](https://github.com/Adrienbannwarth) -->

* [Paartheepan RAVEENTHIRAN](https://github.com/Punkte)  
* [Etienne MELA](https://github.com/EtienneMela)  
* [Adrien BANNWARTH](https://github.com/Adrienbannwarth)  

## Instances
We are using Scaleway's instances.  

> Scaleway's selected servers provides more environmentally friendly services, using simultaneously direct air cooling combined with an adiabatic system.    

Our instance IPs list is in the following file : [./automation/inventory/hosts](./automation/ansible/inventory/hosts)  

## Automation

Change directory to [automation/ansible](./automation/ansible)
### Setup
Install ansible roles :
```
$ ansible-galaxy role install -r ./requirements.yml -p ./roles 
```
In order to accelerate github runner's deployment `roles` are commited and not ignored.

### Deployment

Write the vault pass in file named `.vault_pass`.  

Launch the following command : 
```
$ ansible-playbook ./production.yml -i ./inventory/hosts  --key /path/to/ssh-private-key --vault-password-file ./.vault_pass
```

### Ansible roles
* common: make a `apt-get update` on the server
* docker: Install docker on the server
* pip: Install python on the server
* site: Install python docker, docker-compose modules on the server and launch `docker-compose up` on the server.