# Ansible server Deployment

The Whole server is setup using [Ansible](https://github.com/ansible/ansible).

[Molecule](https://github.com/ansible-community/molecule) is used for Testing the Role against automatically provisioned VMs.
The VMs will be automatically created by [Vagrant](https://github.com/hashicorp/vagrant).

## Requirements

```bash
sudo apt install python3-pip
sudo python3 -m pip install pipenv
pipenv install
```

## Usage

```bash
# Switch to Python Venv
pipenv shell

## All Ansible commands are now available
```

# Testing

Testing is done with Molecule.
Molecule check will Create a VM and deploy a Dev server.
Make sure to overwrite default Variables like the Domainname.

```bash
sudo apt install virtualbox vagrant
pipenv shell
sudo ./molecule/default/forwardports.sh # forwards 80 and 443 of Host to 8080 and 8043.
molecule converge # To Create and Provision the deployment
molecule login # To ssh into the VM
```


## Speed up Testing

You can temporarily comment out roles in [main.yml](./main.yml).