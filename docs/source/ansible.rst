.. _Ansible:

Ansible
========
We install and deploy the system against HPC nodes by Ansible, which is an IT automation engine.

.. note::
   For more information on Ansible installation, please refer to `<http://docs.ansible.com/ansible/latest/intro_installation.html>`_
   
Ansible Inventory Configuration
--------------------------------
Ansible does different tasks against different nodes. Ansible’s inventory, which locates at ``/etc/ansible/hosts``, manages the information of all the used nodes. The configuration for our Ansible's inventory is shown as bellow.

.. _servers:

.. code-block:: yml

   [web]
   web.esciencecloud.sdu.dk
   [index]
   index.esciencecloud.sdu.dk
   [db]
   db.esciencecloud.sdu.dk
   [irods]
   irods[1:2].esciencecloud.sdu.dk
   [ceph-mon]
   cephmon[1:3].esciencecloud.sdu.dk
   [ceph-osd]
   cephosd[1:2].esciencecloud.sdu.dk

Ansible Playbooks and Roles
------------------------------
Each ``.yml`` file is a playbook to complete a single or series tasks. For example, in our case, ``db.yml`` installs and configures PostgreSQL while ``elk.yml`` installs and configures the entire ELK Stack respectively. Below is the tree structures of some playbook examples and their roles within the project.

Playbooks

.. code-block:: bash
   
   ├── confluent.yml
   ├── db.yml
   ├── elk-client.yml
   ├── elk.yml
   ├── irods-re-audit.yml
   ├── irods.yml


Roles

.. code-block:: bash

   ├── confluent
   │   └── tasks
   │       └── main.yml
   ├── db-icat
   │   ├── defaults
   │   │   └── main.yml
   │   ├── files
   │   ├── tasks
   │   │   └── main.yml
   │   └── templates
   ├── db-sducloud
   │   ├── defaults
   │   │   └── main.yml
   │   ├── files
   │   ├── tasks
   │   │   └── main.yml
   │   └── templates
   ├── elasticsearch
   │   ├── defaults
   │   │   └── main.yml
   │   ├── files
   │   │   └── elasticsearch.repo
   │   ├── tasks
   │   │   └── main.yml
   │   └── templates
   │       └── java.sh.j2
   ├── filebeat
   │   ├── defaults
   │   │   └── main.yml
   │   ├── files
   │   │   └── elastic.repo
   │   ├── tasks
   │   │   ├── configurations.yml
   │   │   └── main.yml
   │   └── templates
   │       ├── filebeat.conf.j2
   │       └── filebeat-default.conf.j2
   ├── irods
   │   ├── defaults
   │   │   └── main.yml
   │   ├── files
   │   │   ├── epel.repo
   │   │   └── renci-irods.repo
   │   ├── tasks
   │   │   ├── configurations.yml
   │   │   ├── downgrade.yml
   │   │   ├── main.yml
   │   │   └── upgrade.yml
   │   └── templates
   │       └── irods-environment.conf.j2
   ├── irods-re-audit
   │   ├── defaults
   │   │   └── main.yml
   │   ├── files
   │   ├── tasks
   │   │   ├── configurations.yml
   │   │   └── main.yml
   │   └── templates
   │       ├── irods-cmake.sh.j2
   │       └── server.conf.j2
   ├── kibana
   │   ├── defaults
   │   │   └── main.yml
   │   ├── files
   │   │   └── kibana.repo
   │   ├── tasks
   │   │   └── main.yml
   │   └── templates
   ├── logstash
   │   ├── defaults
   │   │   └── main.yml
   │   ├── files
   │   │   └── logstash.repo
   │   ├── tasks
   │   │   ├── configurations.yml
   │   │   └── main.yml
   │   └── templates
   │       └── audit.conf.j2
   └── postgresql
       ├── defaults
       │   └── main.yml
       ├── files
       ├── tasks
       │   ├── configurations.yml
       │   └── main.yml
       └── templates
           └── postgres.sh.j2

.. note:
   For more information on how we use Ansible to install, configure and deploy, please refer to `<https://github.com/SDU-eScience/Ansible>`_
