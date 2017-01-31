ntp
===

[![Build Status](https://travis-ci.org/resmo/ansible-role-ntp.png?branch=master)](https://travis-ci.org/resmo/ansible-role-ntp)

This role enables users to install and configure ntp on their hosts.

Requirements
------------

This role requires Ansible 1.4 or higher, and platform requirements are listed
in the metadata file.

Examples
--------

1) Install ntp and set the default settings.

	- hosts: all
	  roles:
	    - role: ntp

2) Install ntp and set some custom servers.

	- hosts: all
	  roles:
	    - role: ntp
	      ntp_config_server: [2.ubuntu.pool.ntp.org, 1.ubuntu.pool.ntp.org]

License
-------

BSD

Author Information
------------------

- Benno Joy
- René Moser

