# Ansible Role: Apache Solr

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-solr.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-solr)

An Ansible Role that installs Apache Solr on Linux servers.

## Requirements

Java must be available on the server. You can easily install Java using the `geerlingguy.java` role.

This role is currently tested and working with Solr 3.x and 4.x; 5.x is not yet fully tested.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    solr_workspace: /root

Files will be downloaded to this path on the remote server before being moved into place.

    solr_create_user: true
    solr_user: solr

Solr will be run under Jetty as the `solr_user`. Set `solr_create_user` to `false` if `solr_user` is created before this role runs.

    solr_version: "4.10.4"

The Apache Solr version to install.

    solr_mirror: "https://archive.apache.org/dist"

The Apache Project mirror from which the Solr tarball will be downloaded. In case of slow download speed or timeouts it is useful to set the mirror to the one suggested by Apache's [mirror download site](https://www.apache.org/dyn/closer.cgi/lucene/solr/).

    solr_install_path: /opt/solr

The path where Apache Solr will be installed.

    solr_home: /var/solr

The path where local Solr data (search collections and configuration) will be stored. Should typically be outside of the `solr_path`, to make Solr upgrades easier.

    solr_log_file_path: /var/log/solr.log

Path where Solr log file will be created.

    solr_host: "0.0.0.0"

The hostname or IP address to which Solr will bind. Defaults to `0.0.0.0` which allows Solr to listen on all interfaces.

    solr_port: "8983"

The port on which Solr will run.

    solr_xms: "256M"
    solr_xmx: "512M"

Memory settings for the JVM. These should be set as high as you can allow for best performance and to reduce the chance of Solr restarting itself due to OOM situations.

## Dependencies

None.

## Example Playbook

    - hosts: solr-servers
      roles:
        - { role: geerlingguy.java }
        - { role: geerlingguy.solr }

## License

MIT / BSD

## Author Information

This role was created in 2014 by [Jeff Geerling](http://jeffgeerling.com/), author of [Ansible for DevOps](http://ansiblefordevops.com/).
