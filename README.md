apache
========

This role installs and configures Apache

[![Build Status](https://drone-opsdev.rax.io/github.com/rack-roles/apache/status.svg?branch=master)](https://drone-opsdev.rax.io/github.com/rack-roles/apache)

Requirements
------------

No requirements.

Role Variables
--------------

### Playbook Variables
* `apache_vhost_create_default`: True
* `apache_vhost_create_docroots`: True
  
### Apache Directives
* `apache`:
 * `accessfilename`: .htaccess
 * `keepalive_enabled`: "Off"
 * `keepalive_max_requests`: 100
 * `keepalive_timeout`: 15
 * `listen_port`: 80
 * `listen_port_ssl`: 443
 * `mpm_maxconnectionsperchild`: 0  # >= 2.3.9
 * `mpm_maxrequestworkers`: 0
 * `mpm_prefork_startservers`: 8
 * `mpm_prefork_minspareservers`: 5
 * `mpm_prefork_maxspareservers`: 20
 * `mpm_prefork_serverlimit`: 256
 * `mpm_prefork_maxclients`: 256
 * `mpm_prefork_maxrequestsperchild`: 4000
 * `mpm_worker_startservers`: 4
 * `mpm_worker_maxclients`: 300
 * `mpm_worker_minsparethreads`: 25
 * `mpm_worker_maxsparethreads`: 75
 * `mpm_worker_maxrequestsperchild`: 0
 * `mpm_worker_threadsperchild`: 25
 * `mpm_worker_serverlimit`: 256
 * `timeout`: 60

* `apache_vhosts`: List of virtual hosts.

#### Example Apache Vhost
```
apache_vhosts:
  servername: "example.com"
  serveralias: "www.example.com"
  documentroot: "/var/www/html/vhosts/example.com"
  directoryindex: "index.php"
  serveradmin: "webmaster@example.com"
  extra_parameters: "Directive values"
```

Dependencies
------------

There are no external dependencies.

Example Playbook
-------------------------

Here is a simple example playbook:

    ---
    - hosts: all
      roles:
        - { role: Rackspace_Automation.apache, x: 42 }

License
-------

BSD

Author Information
------------------

[Rackspace - the open cloud company](http://rackspace.com)

Ask about our DevOps Automation Service - [www.rackspace.com/devops](http://rackspace.com/devops)
