# New node setup with Ansible

This guide is for setting up new nodes.

## First run (brand new node)

1. Use `ssh-copy-id` to copy the local SSH key to the machine:

   ```bash
   $ ssh-copy-id {user}@{host}
   ```

2. Verify you can ssh into the machine using the ssh key:

   ```bash
   $ ssh {host}
   ```

3. Run the `host-setup` Ansible playbook on the host, providing the machine's
   `root` password (`-K`).

   In Debian 13.7.0, configuring a `root` password omits the intsallation of
   `sudo`, so this extra parameter is not necessary on subsequent runs.

   ```bash
   $ ansible-playbook host-setup.yml -K --become-method=su
   ```

## Subsequent runs (updates)

1. Run the `host-setup` Ansible playbook on the host, providing the ansible user
   (`max`)'s password (`-k`):

   ```bash
   $ ansible-playbook host-setup.yml -K
   ```
