`dimmaryanto93.sonatype_nexus_oss`
=========

Repository ini digunakan untuk menginstall [Sonatype nexus-oss](https://www.sonatype.com/products/repository-oss) untuk Linux

Support platform

- Debian
- Ubuntu
- CentOS


Ansible - User Guide
------------

Persiapan yang harus di lalukan, diantaranya

1. Create new user on your server, Recomend using **very-very Strong Password** or using password generator. 
  ```bash
  adduser <username>
  ```

2. Granted to sudoers with NOPASSWD, using `visudo`
  ```ini
  username    ALL=(ALL) NOPASSWD:ALL
  ```

3. Authenticate with private-key for login ssh, generate ssh key on your local machine then use `ssh-copy-id user@your-ip-server` to copy public key to your server.


Requirements
------------

Untuk menggunakan role ini, kita membutuhkan package/collection 

- [ansible.posix](https://github.com/ansible-collections/ansible.posix)
- [community.general](https://github.com/ansible-collections/community.general)

Temen-temen bisa install, dengan cara 

```bash
ansible-galaxy collection install ansible.posix community.general
```

Atau temen-temen bisa menggunakan `requirement.yaml` file and install menggunakan `ansible-galaxy collection install -r requirement.yaml`, dengan format seperti berikut:

```yaml
---
collections:
  - community.general
  - ansible.posix
```

Role Variables
--------------

Ada beberapa variable yang temen-temen bisa gunakan untuk setting sonatype nexus-oss, diantaranya seperti berikut:

| Variable name                 | Example value       | Description |
| :---                          | :---                | :---        |
| `nexus_download_url`          | `https://download.sonatype.com/nexus/3/latest-unix.tar.gz` | Download link latest version untuk linux |
| `nexus_installation_path`     | `/opt/nexus`        | Default extract / installation folder |
| `nexus_user`                  | `nexus`             | Normal user for running nexus service |
| `nexus_default_port`          | `8081`              | Default port for web admin console    |
| `nexus_admin_password_print`  | `true`              | Show default password for user admin to login |

Dependencies
------------

Untuk mengginstall Sonatype Nexus OSS kita membuatuhkan Java Development Kit (JDK) sesuai dengan requirment dari official websiste [seperti berikut](https://help.sonatype.com/repomanager3/installation/system-requirements#SystemRequirements-Linux)

Kita bisa menggunakan role [oracle_java](https://galaxy.ansible.com/dimmaryanto93/oracle_java) atau install manualy


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```ansible
- hosts: servers
  become: true
  roles:
      - { role: dimmaryanto93.sonatype_nexus_oss }
```

License
-------

MIT
