- [First Project](#first-project)

*Inventories organize managed nodes in centralized files that provide Ansible with system information and network locations. Using an inventory file, Ansible can manage a large number of hosts with a single command.*

## First Project

- Create a project folder (vm): `mkdir -p ~/Documents/ansible/ansible_quickstart && cd ~/Documents/ansible/ansible_quickstart`
- Create a file named `inventory.yaml` (vm): `touch inventory.yaml`
- Add the IP address of the VM to the `vi inventory.yaml` (vm):

```yaml
myhosts:
  hosts:
    localhost:
      ansible_connection: local
      # ansible_host: 192.168.1.9 # If you want to connect to a remote host
      # http_port: 80 # If you want to define a variable
```

- You can add multiple hosts to the inventory file. 
- Test the inventory file (vm): `ansible-inventory --list`
- Test the connection to the localhost (vm): `ansible myhosts -m ping -i inventory.yaml`