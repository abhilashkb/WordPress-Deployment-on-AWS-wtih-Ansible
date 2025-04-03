# Nginx Setup Role

This Ansible role is designed to install and configure Nginx as a web server for hosting WordPress. It also installs PHP and its required extensions to ensure WordPress runs smoothly.

## Requirements

- Ansible 2.9 or later.
- The target system should be a Debian-based Linux distribution (e.g., Ubuntu).
- Ensure the `apt` module is available for package management.
- Sudo privileges are required to install and configure packages.

## Role Variables

The following variables can be set to customize the role:

| Variable Name            | Default Value       | Description                                                                 |
|--------------------------|---------------------|-----------------------------------------------------------------------------|
| `nginx_config_template`  | `wordpress.conf.j2` | The Jinja2 template file for the Nginx configuration.                      |
| `php_version`            | `7.4`              | The PHP version to install and configure.                                  |
| `wordpress_root`         | `/var/www/wordpress`| The root directory where WordPress files will be hosted.                   |
| `nginx_user`             | `www-data`         | The user under which Nginx will run.                                       |
| `nginx_group`            | `www-data`         | The group under which Nginx will run.                                      |

You can override these variables in your playbook or inventory file.

## Dependencies

This role does not depend on any other roles. However, it assumes that the target system has basic networking and SSH access configured.

## Tasks Performed

1. Updates the system's package cache.
2. Installs the following packages:
   - Nginx
   - PHP and required extensions:
     - `php-fpm`
     - `php-mysql`
     - `php-curl`
     - `php-xml`
     - `php-mbstring`
     - `php-zip`
     - `php-gd`
     - `php-bcmath`
     - `php-json`
     - `php-xmlrpc`
     - `php-soap`
   - MariaDB server and client.
3. Configures PHP-FPM for WordPress.
4. Configures Nginx using a custom template.
5. Ensures proper permissions for the WordPress directory.

## Example Playbook

Here’s an example of how to use this role in your playbook:

```yaml
- name: Configure Nginx for WordPress
  hosts: wordpress_servers
  become: true
  roles:
    - role: nginx_setup
      vars:
        nginx_config_template: wordpress.conf.j2
        php_version: 7.4
        wordpress_root: /var/www/wordpress
```

## License

BSD

## Author Information

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
