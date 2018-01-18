.. _iRODS:

iRODS
=====
iRODS is an open source data management software used by research organizations and government agencies worldwide. It is a middleware which in our case sits above the Ceph filesystem and our application. Our iRODS deployment includes an iRODS Metadata Catalog(iCAT) database and two iRODS servers.
 
iCAT Database Instance Setups
-------------------------------
iRODS neither creates nor manages a database instance itself, just the tables within the database. Therefore, the database instance should be created and configured before installing iRODS. :ref:`PostgreSQL` is the database server for us which is used to implement the iCAT database. ``db.yml`` is the playbook for handling database related tasks. The ``db-icat`` role creates the irods user, ICAT database and grant all the permissons. Run ``\l`` to view databases and permissions.

.. code-block:: psql

    postgres=# \l

                                      List of databases
    Name   |Owner    |Encoding |Collate    |Ctype      |Access privileges
    -------+---------+---------+-----------+-----------+-----------------------
    ICAT   |postgres |UTF8     |en_US.UTF-8|en_US.UTF-8|=Tc/postgres+
           |         |         |           |           |postgres=CTc/
           |         |         |           |           |postgres+
           |         |         |           |           |irods=CTc/p


iRODS Server Installation
-----------------------------------
* Playbook: irods.yml

* Role: irods

* Version and Dependencies
 
 * 4.2.1

.. note::

   For more information on our iRODS installation and configuration, please refer to

   `<https://github.com/SDU-eScience/Ansible/blob/master/irods.yml>`_

   `<https://github.com/SDU-eScience/Ansible/tree/master/roles/irods>`_
  

iRODS Server Configuration
------------------------------------
After installation, run ``setup_irods.py`` script to fullfil information of the iRODS server.

.. code-block:: text-only

   $ (sudo) python /var/lib/irods/scripts/setup_irods.py


The asked information is shown as below

.. code-block:: text-only

   1. Service Account
      Service Account Name
      Service Account Group
      Catalog Service Role
   2. Database Connection
      ODBC Driver
      Database Server's Hostname or IP
      Database Server's Port
      Database Name
      Database User
      Database Password
      Stored Passwords Salt
   3. iRODS Server Options
      Zone Name
      Zone Port
      Parallel Port Range (Begin)
      Parallel Port Range (End)
      Control Plane Port
      Schema Validation Base URI
      iRODS Administrator Username
   4. Keys and Passwords
      zone_key
      negotiation_key
      Control Plane Key
      iRODS Administrator Password
   5. Vault Directory

Once a iRODS server is up and running, you can view the environment settings by running

.. code-block:: text-only

   $ ienv


