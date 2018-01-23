.. _Ceph:

Ceph
====

Ceph Overview
-------------

Ceph is an open-source, massively scalable, software-defined storage system which provides object, block and file system storage from a single clustered platform.

Ceph Storage Cluster
--------------------
Ceph storage cluster deployments begin with setting up each Ceph Node, network and the Ceph Storage Cluster. A Ceph Storage Cluster requires at least one Ceph Monitor and at least two Ceph OSD Daemons. Our Ceph storage cluster includes five nodes - three nodes for Ceph monitors and two nodes for Ceph OSDs. Additional, three Ceph-mgrs have been set up on each of the nodes which is running a Ceph-mon daemon. By default, whichever Ceph-mgr instance comes up first will be made active by the monitors, and the others will be standbys. The following shows the information of our Ceph storage cluster.

.. figure::  images/ceph_storage_cluster_original_crop_bright.png
   :align:   center


Ceph Installation
-----------------
We use :ref:`Ansible` to install and configure Ceph through `the official community Ceph repositories <http://download.ceph.com>`_.

Playbook
^^^^^^^^
Our configuration that deploys ``luminous`` version of Ceph with OSDs:

.. code-block:: yml

   ceph_origin = repository
   ceph_repository = community
   ceph_stable_release: luminous
   monitor_interface: eno49
   osd_scenario: non-collocated


.. note::

   For more information on our Ceph ansible playbooks please refer to 
   `<https://github.com/SDU-eScience/eScienceCloud/tree/master/playbooks/ceph>`_

Prometheus Plugin and Grafana
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The Ceph Prometheus plugin provides a Prometheus exporter to pass on Ceph performance counters from the collection point in Ceph-mgr. The exported data can be queried from Grafanawhich allows us to query, visualize, alert on the Ceph metrics. The following shows a Grafana dashboard which queries Prometheus for Ceph data.

.. figure::  images/grafana.png
   :align:   center


iRODS RADOS Resource Plugin
---------------------------
This iRODS plugin implements a direct access to Ceph/rados in the most efficient manner. Files in the iRODS namespace are mapped to objects in the rados key-blob store. In contrast to other plugins, the irados resource plugin does not need to cache or stage files, but gives you direct and parallel access to data. Internally, the plugin maps the POSIX like open, read, write, seek, unlink,stat, and close calls to the librados client's operations. To fully use the inherent rados cluster parallelity, iRODs files are split to multiple 4 MB files and uploads of large files open multiple parallel transfer threads.
