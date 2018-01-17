.. eScienceCloud documentation master file, created by
   sphinx-quickstart on Fri Aug 18 12:10:07 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to SDUCloud's documentation!
=============================================

This documentation exists to provide an introduction of the  SDUCloud. The project aims to provide easy access to national HPC infrastructures,like the Abacus 2.0 supercomputer,allowing a researcher to run complex or heavy computations on a supercomputer in a completely seamless and automatic way. 


Overview, by components
========================
* :ref:`Ansible`
* :ref:`Ceph`
* :ref:`iRODS`
* :ref:`Zookeeper`
* :ref:`Kafka`
* :ref:`Filebeat`
* :ref:`Logstash`
* :ref:`Elasticsearch`
* :ref:`Kibana`
* :ref:`PostgreSQL`
* :ref:`Pgpool_II`

Overview, by design
===================
* UI
 * :ref:`Ktor`
 * :ref:`React`
* Service
 * Authentication service
  * :ref:`WAYF`
  * :ref:`JSON Web Token(JWT)`
 * HPC related service 
  * :ref:`app-service`
  * :ref:`auth-service`
 * Storage related service
  * :ref:`upload-service`
  * :ref:`storage-service`
 * Data analysing service
  * :ref:`elastic-service`
 * Data auditing service
  * :ref:`iRODS_Re_Audit_Plugin`
 * Logging service
  * :ref:`kafka`
* Database
 * :ref:`iCAT`
 * :ref:`SDUClouddb`

.. toctree::
   :maxdepth: 2
   :caption: Contents:
   
Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

