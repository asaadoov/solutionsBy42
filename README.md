


# Ansible Role: Passbolt

![Passbolt Logo](https://www.passbolt.com/images/passbolt_logo.png)

## Overview

This Ansible role automates the installation and configuration of Passbolt, an open-source password manager, on Ubuntu 20.04 VMs. It is designed to ensure consistency and efficiency in setting up Passbolt across development and testing environments.

## Requirements

- Ansible installed on the control machine
- Ubuntu 20.04 VMs for deployment
- Vagrant for local testing (optional)

## Role Structure

```
passbolt/
|-- defaults/
|   `-- main.yml
|-- handlers/
|   `-- main.yml
|-- tasks/
|   |-- backup.yml
|   |-- main.yml
|   |-- ssl.yml
|   `-- main.yml
|-- templates/
|   |-- passbolt.php.j2
|   `-- passbolt.nginx.conf.j2
|-- .gitignore
|-- LICENSE
|-- README.md
|-- vagrant.yml
`-- requirements.yml
```

## Role Variables

- `passbolt_database_user`: Passbolt database user
- `passbolt_database_password`: Passbolt database password
- `passbolt_database_name`: Passbolt database name
- `passbolt_app_key`: Generated Passbolt app key
- `passbolt_security_salt`: Generated Passbolt security salt
- `passbolt_ssl_enabled`: Enable SSL/TLS (default: false)
- `passbolt_backup_enabled`: Enable automated backups (default: true)

For more variables, check `defaults/main.yml`.

## Dependencies

None

## Usage

1. Install the role using Ansible Galaxy:

   ```bash
   ansible-galaxy install your_username.passbolt
   ```

2. Create an Ansible playbook (`passbolt.yml`):

   ```yaml
   ---
   - name: Deploy Passbolt
     hosts: your_passbolt_servers
     become: yes
     roles:
       - your_username.passbolt
   ```

3. Run the playbook:

   ```bash
   ansible-playbook -i your_inventory.ini passbolt.yml
   ```

## Vagrant Integration

For local testing, use the provided `vagrant.yml` playbook:

```bash
ansible-playbook -i inventory/vagrant.ini vagrant.yml
```

## SSL/TLS Configuration

If `passbolt_ssl_enabled` is set to true, a self-signed SSL certificate will be generated.

## Automated Backups

If `passbolt_backup_enabled` is set to true, automated backups are scheduled daily at 3:00 AM using cron.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
