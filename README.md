# Deploy a SWARM cluster with one command line

## Description

This playbook provision a swarm cluster and deploy a management stack with Traefik Frontend, Portainer and Portainer Agents


## Requeriments

### Have a ubuntu16 template in Vmware

###Install requirements:

sudo apt-get install python-pip ansible sshpass

pip install pyvmomi


## Config

1. Edit the `inventory` file by setting the Hostnames, Ip and other information about the vms that will be created.
2. Edit the file `/roles/deploy_vm/vars/vars.yml` to adjust the following settings:
    * Infrastructure (Where provisioning vms)
    * The processor, disk, and memory settings of vms
3. Edit `/roles/environment/templates/management.yml.j2`  and change the volume driver to whatever you need in your environment.
4. Check and edit `/roles/swarm_provision/files/traefik.toml` to setup your frontend and put your SSL certificate into.

## Exec

```
ansible-playbook -i inventory DEPLOY_SWARM.yml --user root --ask-pass
```