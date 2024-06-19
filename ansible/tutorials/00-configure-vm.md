- [Configure a VM for Ansible](#configure-a-vm-for-ansible)
- [Install Ansible on the VM](#install-ansible-on-the-vm)
- [Ansible Config](#ansible-config)
- [Optional Configuration](#optional-configuration)
  - [Install virtualbox command line](#install-virtualbox-command-line)

In this ansible learning path, we will use a Linux Mint VM to install and run Ansible.

- VM: Oracle VM VirtualBox 7.0.10
- Host: Linux Mint 21.3

If "(vm)" is written after a command, it means that the command should be run on the VM. If "(host)" is written after a command, it means that the command should be run on the host machine.

## Configure a VM for Ansible

- Create a Linux Mint VM using VirtualBox Manager.
- Install and upgrade Linux Mint on the VM.
- Change network settings on VM: Settings -> Network -> Adapter 1 -> Attached to: Bridged Adapter
- Get IP address (vm): `ifconfig`
- Try to connect to the VM using SSH (host): `ssh bulmust@192.168.1.112`
  - If connection is refused, check the firewall settings (vm): `sudo ufw status`. It should be `inactive`.
  - If connection is refused, check the SSH service status (vm): `sudo systemctl status sshd`. If sshd could not be found, install it (vm): `sudo apt-get install openssh-server`. Check the status again.
- Copy the public key from the host to the VM (host): `ssh-copy-id bulmust@192.168.1.112`. Check (host) `ssh bulmust@192.168.1.112`. It should not ask for password.

## Install Ansible on the VM

- Install pip (vm): `sudo apt-get install python3-pip -y`
- Install Ansible (vm): `pip install ansible`
- Add `/home/bulmust/.local/bin` to the PATH (vm): `echo 'export PATH=$PATH:/home/bulmust/.local/bin' >> ~/.bashrc`
- Restart the shell (vm): `source ~/.bashrc`
- Check the Ansible version (vm): `ansible --version`

## Ansible Config

- Create a sample ansible.cfg file (vm): `ansible-config init --disabled > ~/.ansible.cfg`

## Optional Configuration

### Install virtualbox command line

Install virtualbox command line on your localhost if it is not installed `sudo apt-get install virtualbox`.

The VM name is `bulmust.learning`, so if you want to
  - start the vm `VBoxManage startvm bulmust.learning --type headless`
  - stop the vm `VBoxManage controlvm bulmust.learning acpipowerbutton`