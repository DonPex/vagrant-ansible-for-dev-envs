# vagrant-ansible-for-dev-envs
A collection of Vagrantfiles and Ansible playbooks to configure a portable development environment in a VM.
Useful to setup quickly fresh environments ready to develop or test apps.

## Requirements
- Virtualbox or VMWare
- Vagrant 

## Usage
Once installed Vagrant, choose an available environment (e.g. "Java"), go into that folder and run via terminal (Powershell for Windows, Shell for Unix):

```vagrant up```

To automatically download and set up a Virtual Machine with everything you have specified in Vagrantfile and playbook already setup.

To install only new provisioned tools, after starting the VM run:

```vagrant provision```

You can customize versions and tools just modifying the playbook.yml.

## Available configs and what is included
- **Java**: JDK 1.8, Maven 3.8.4 Docker, Docker-compose (latest).

## Possible improvements
- Avoid repeated provisioning from Ansible
- Use vars in playbook (not working for "roles")
