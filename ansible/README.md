# Basic Ansible Commands

Ansible is an open-source tool for automating configuration management, application deployment, and task orchestration.

## Ansible Architecture Overview

<!-- ![Ansible Architecture](https://docs.ansible.com/ansible/latest/_images/ansible_architecture.png) -->

The diagram above shows Ansible's architecture with the control node managing multiple target hosts through SSH connections.

> [!IMPORTANT]
> Ansible uses SSH to connect to managed hosts and doesn't require any agents to be installed on target systems.
> 
> Ensure SSH keys or credentials are configured for target hosts.

- **Check Ansible version**  
    ```bash
    ansible --version
    ```
    Displays the installed `Ansible` version.

- **Run an ad-hoc command**  
    ```bash
    ansible <host_pattern> -m <module> -a "<arguments>"
    ```
    Executes a single command on specified hosts (e.g., `ansible all -i inventory.ini -m ping` to test connectivity).

- **List available hosts**  
  ```bash
  ansible all -i inventory.ini --list-hosts
  ```
  Shows all hosts defined in the inventory file.

## Ansible Inventory

<!-- ![Inventory Structure](https://docs.ansible.com/ansible/latest/_images/inventory_structure.png) -->

The inventory file defines the hosts and groups that Ansible manages. It can be static (INI/YAML format) or dynamic (generated from external sources).

- **List inventory groups**  
  ```bash
  ansible-inventory --list
  ```
  Displays the inventory configuration in JSON format.

- **List inventory hosts**  
  ```bash
  ansible-inventory --list --yaml
  ```
  Displays the inventory in YAML format.

- **Test connectivity to hosts**  
  ```bash
  ansible <host-pattern> -m ping
  ```
  Pings all specified hosts to verify connectivity.

- **Test with specific inventory file**  
  ```bash
  ansible -i <inventory_file> <host-pattern> -m ping
  ```
  Uses a specific inventory file instead of the default.

- **Copy a file to hosts**  
  ```bash
  ansible <host-pattern> -m copy -a "src=/local/path dest=/remote/path"
  ```
  Copies a file from the control node to the target hosts.

- **Install a package**  
  ```bash
  ansible <host-pattern> -m apt -a "name=<package> state=present"  # For Debian/Ubuntu
  ansible <host-pattern> -m yum -a "name=<package> state=present"  # For RHEL/CentOS
  ```
  Installs a package on target hosts using the appropriate package manager.

- **Run a command on hosts**  
  ```bash
  ansible <host-pattern> -m shell -a "<command>"
  ```
  Executes a shell command on specified hosts (e.g., `ansible all -m shell -a "uptime"`).

## Ansible Playbooks

<!-- ![Playbook Structure](https://docs.ansible.com/ansible/latest/_images/playbook_structure.png) -->

Playbooks are YAML files that define automation tasks and can be used to configure systems, deploy software, or orchestrate complex workflows.

- **Check playbook syntax**  
  ```bash
  ansible-playbook <playbook.yml> --syntax-check
  ```
  Validates the syntax of a playbook without running it.

- **Dry run a playbook**  
  ```bash
  ansible-playbook <playbook.yml> --check
  ```
  Simulates playbook execution without making changes on hosts.

- **Run a playbook**  
  ```bash
  ansible-playbook -i inventory.ini <playbook.yml>
  ```
  Executes a playbook (YAML file) to automate tasks on target hosts.

- **Run playbook with specific tags**  
  ```bash
  ansible-playbook -i inventory.ini <playbook.yml> --tags "tag1,tag2"
  ```
  Executes only tasks with specified tags.

- **Run playbook with limit**  
  ```bash
  ansible-playbook -i inventory.ini <playbook.yml> --limit "host1,host2"
  ```
  Runs the playbook only on specified hosts.

## Configuration and Playbook Tips

> [!NOTE]
> 
> - **Inventory file**: Define hosts in `/etc/ansible/hosts` or a custom file (e.g., `ansible -i inventory.yml ...`).
> - **Playbook structure**: A playbook is a YAML file with tasks, roles, and variables (e.g., `tasks: - name: Install nginx ...`).
> - **Modules**: Use modules like `apt`, `yum`, `file`, `service`, or `copy` for common tasks.
> - **Variables**: Define variables in playbooks or separate files for reusable configurations.

> [!TIP]
> 
> - **Verbose output**: Add `-v`, `-vv`, or `-vvv` to commands for detailed debugging output.
> - **Help**: Use `ansible-doc <module>` for module documentation (e.g., `ansible-doc copy`).

[Go Back](../README.md)