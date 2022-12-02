# Prerequisite

- Ansible installed on the control machine
  - Follow https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html
  - Or, you can use the DevContainer with VSCode.
- Password-less SSH into a remote host as a normal user
  - Configure `~/.ssh/authorized_keys` to enable this.
- Password-less sudo as a normal in the remote host
  - Edit `/etc/sudoers` file to enable this.

# Run

- Copy and modify `./inventory.example.ini` to `./inventory.ini`. Make the changes required
  to suit the environment you are working in.
- Verify ansible and your inventoryh works by running: `ansible -i ./inventory.ini myserver -m ping`.
  - You should see someting like:
  ```
    [YOUR_HOST_NAME/IP] | SUCCESS => {
      "ansible_facts": {
          "discovered_interpreter_python": "/usr/bin/python3"
      },
      "changed": false,
      "ping": "pong"
  }
  ```
- Copy `docker-compose.example.yaml` file and create `docker-compose.yaml`, then run the playbook
  `ansible-playbook -i ./inventory.ini ./playbook.yaml`
- Check everything works by visiting the configured host/port, in the example it should be
  - 10.0.10.25:8080
  - 10.0.10.25:8081