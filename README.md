# Role Name

Apache 2.x for RHEL/CentOS 6.x by geerlingguy.

## Requirements

None.

## Role Variables

Available variables are listed below, along with the default value (see `vars/main.yml`):

    apache_listen_port: 80

The port on which apache should be listening. Useful if you have another service (like a reverse proxy) listening on port 80.

    apache_vhosts:
      # Additional optional properties: 'serveradmin, extra_parameters'.
      - {servername: "local.dev", documentroot: "/var/www/html"}

Add a set of properties per virtualhost, including `servername` (required), `documentroot` (required), `serveradmin` (optional: the admin email address for this server), and `extra_parameters` (you can add whatever you'd like in here).

Note that this role doesn't configure SSL support out of the box; you would need to add in additional tasks to listen on port 443 and add your own VirtualHost directives for SSL. This may be improved in the future :)

## Dependencies

  - geerlingguy.repo-epel (Installs the EPEL repository for CentOS 6.x).

## Example Playbook

    - hosts: webservers
      vars_files:
        - vars/main.yml
      roles:
        - { role: geerlingguy.apache }

*Inside `vars/main.yml`*:

    apache_listen_port: 8080
    apache_vhosts:
      - {servername: "example.com", documentroot: "/var/www/vhosts/example_com"}

## License

MIT / BSD

## Author Information

This role was created in 2014 by Jeff Geerling (@geerlingguy), author of Ansible for DevOps. You can find out more about the book at http://ansiblefordevops.com/, and learn about the author at http://jeffgeerling.com/.
