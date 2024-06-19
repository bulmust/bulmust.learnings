
- [Create a Playbook](#create-a-playbook)

*Playbooks are automation blueprints, in YAML format, that Ansible uses to deploy and configure managed nodes.*

- *Playbook: A list of plays that define the order in which Ansible performs operations, from top to bottom, to achieve an overall goal.*
- *Play: An ordered list of tasks that maps to managed nodes in an inventory.*
- *Task: A reference to a single module that defines the operations that Ansible performs.*
- *Module: A unit of code or binary that Ansible runs on managed nodes. Ansible modules are grouped in collections with a Fully Qualified Collection Name (FQCN) for each module.*

## Create a Playbook

Create a playbook file named `~/Documents/ansible/ansible_quickstart/playbook.yaml` in the project folder (vm).

```yaml
- name: My first playbook
  hosts: myhosts
  tasks:
    - name: Ping my hosts
      ansible.builtin.ping:

    - name: Print a message
      ansible.builtin.debug:
        msg: Hello, Ansible!
```