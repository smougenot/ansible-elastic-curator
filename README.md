Role elastic-curator
=========

Manage Curator from Elastic team https://github.com/elastic/curator
Only compliant with Curator 5.x

The aim is to :
* install curator from binary package (less dependency)
* setup curator (configuration and actions)
* add launcher script
* add scheduled runs of the launcher
* add log rotation

Requirements
------------

None

Role Variables
--------------

TODO : complete description

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    ---
    - hosts: all
    
      become: yes
    
      vars_files:
        - vars/main.yml
    
    #  vars:
    #    - ansible_python_interpreter: "/usr/bin/env python2.7"
    
      pre_tasks:
      - name: Include OS specific variables
        include_vars: "vars/{{ ansible_os_family }}.yml"
    
      roles:
        - role: java
        - role: elastic.elasticsearch
          tags : ["es"]
          vars:
            es_major_version: "5.x"
            es_version: "5.5.1"
            es_instance_name: "log1"
            es_heap_size: "256m"
            es_enable_xpack: false
            network:
             host: "_eth0_"
            http:
             port: 9200
            transport:
             tcp:
              port: 9300
            node:
             data: true
             master: true
        - role: elastic-curator
          tags : ["curator", "es"]
          

License
-------

Apache 2 (see source repository)

Author Information
------------------

Hope this tool could be transferred to Elastic team 
Else, I hope it may help
