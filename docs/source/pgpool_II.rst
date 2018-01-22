.. _Pgpool_II:

Pgpool-II
==========
Pgpool-II is a middleware which works between PostgreSQL server and a database client. It takes an advantage of the PostgreSQL build-in replication feature to reduce the load on each PostgreSQL server by distributing SELECT queries among multiple servers, improving system's overall throughput.


Pgpool Configuration
---------------------

The pgpool-II user account
^^^^^^^^^^^^^^^^^^^^^^^^^^^
We run Pgpool-II by a Unix user account - pgpool.


.. code-block:: text-only

   $ (sudo) useradd pgpool


Configuring pcp.conf
^^^^^^^^^^^^^^^^^^^^
PCP commands are UNIX commands which manipulate Pgpool-II via the network. A PCP user and password for us has been declared in ``pcp.conf`` in ``/etc`` directory. A user postgres and its associated password has been written as one line using the following format:

.. code-block:: text-only

   postgres:[md5 encrypted password]


[md5 encrypted password] can be produced with the pg_md5 command. The following command used to generate the md5 encrypted password for postgres user for us.

.. code-block:: text-only

   $ pg_md5 your_password
   1060b7b46a3bd36b3a0d66e0127d0517


Configuring pgpool.conf
^^^^^^^^^^^^^^^^^^^^^^^
To set streaming replication mode, we reused the sample configuration file for streaming replication mode from pgpool-II installation. The file is located at ``/etc/pgpool.conf.sample-stream``. The main part of our pgpool-II configrations is shown as below.

Connection settings

  .. code-block:: text-only

     # '*' accepts all incoming connections
     listen_addresses = '*'
     # The port number used by pgpool-II to listen for connections
     port = 9999
     # The directory where the UNIX domain socket accepting connections
     # for pgpool-II will be created
     socket_dir = '/var/run/postgresql/'
     # '*' accepts all incoming connections
     pcp_listen_addresses = '*'
     # The port number used by PCP process to listen for connections
     pcp_port = 9898
     # The directory where the UNIX domain socket accepting connections
     # for pgpool-II will be created
     pcp_socket_dir = '/var/run/postgresql/'


Running mode settings

To enable streaming replication mode in Pgpool-II, firstly turn on the ``master_slave_mode``. By doing this, Pgpool-II can couple with PostgreSQL server  which is responsible for doing the actual data replication.

  .. code-block:: text-only

     # Setting to on enables the master/slave mode
     master_slave_mode = on
     # Suitable for PostgreSQL's built-in streaming replication function
     master_slave_sub_mode = 'stream'

Backend settings

We have three backends which pgpool communicates with. And they all needs to be specified by the parameters as below.

  .. code-block:: text-only

     # Host name or IP address to connect to for backend 0
     backend_hostname0 = 'localhost'
     # Port number for backend 0
     backend_port0 = 5432
     # Weight for backend 0 (only in load balancing mode)
     backend_weight0 = 1
     # Data directory for backend 0
     backend_data_directory0 = '/data'
     # Controls various backend behavior
     # ALLOW_TO_FAILOVER or DISALLOW_TO_FAILOVER
     backend_flag0 = 'ALLOW_TO_FAILOVER'
     backend_hostname1 = 'localhost'
     backend_port1 = 5433
     backend_weight1 = 1
     backend_data_directory1 = '/data1'
     backend_flag1 = 'ALLOW_TO_FAILOVER'
     backend_hostname2 = 'localhost'
     backend_port2 = 5434
     backend_weight2 = 1
     backend_data_directory2 = '/data2'
     backend_flag2 = 'ALLOW_TO_FAILOVER'


Load balancing settings
 
We enabled load balancing so that pgpool-II could send the writing queries to the primay node, and other queries got load balanced among all backend nodes. To which node the load balancing mechanism sends read queries is decided at the session start time and will not be changed until the session ends. 

.. note::

   For more information on which query should be sent to which node in load balancing (streaming replication mode), please refer to `<http://www.pgpool.net/docs/latest/en/html/runtime-config-load-balancing.html>`_
