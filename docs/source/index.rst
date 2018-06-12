.. eScienceCloud documentation master file, created by
   sphinx-quickstart on Fri Aug 18 12:10:07 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to SDUCloud
=============================================

Link:
https://cloud.sdu.dk

Introduction
------------

SDUCloud have been designed and programmed at the eScience Center at the
University Of Southern Denmark. Its components are provided by the open source
community.

The purpose is to provide a user interface that improves the usability of the
HPC environment (Abacus 2.0) for the common user. At the same time it provides a
data storage that secures the data in compliance with GDPR. One of the overall
goals is to improve the searcheability for data that are already stored in
SduCloud. This is done by adding metadata to the stored files in SDUCloud. The
metadata (data about data) are made searchable within the SDUCloud user
interface. Later other search engines can be attached to SDUClouds metadata
service. Another example of the implemantation of "Open Access" is the
integration to Zenodo.


Quick Start
-----------

To get started using SDUCloud please see our quick start guide:
:ref:`quickstart`. This will show you how to access and navigate SDUCloud,
upload/download files and use the applications that are within SDUCloud.

Design features
===============

Security
--------

As part of the GDPR compliance the following design patterns have been
implemented:

Access Controls
---------------

Wayf

Privileged users are proxy users so all none system users are granted the least
privilege.

All duties within the system are handled by micro services that acts on behalf
of the logged in user according to the actual permissions that have been granted
to the users role.

On the technical level all transactions (frontend/backend) are authenticated by
Json Web Tokens https://jwt.io/ (JSR7519) which is granted to each user session
as part of the authorisation process.


.. figure::  images/WAYF.png
   :align:   center


Certificates
------------
Certificates from Digicert have been installed on all servers.


Dataprotection
--------------

Encryption for data at rest and in motion prevents unauthorized access, it is
transparent to applications and users, it provides a strong preventive control,
and modern solutions typically experience low performance impact. Additional
data protection technologies include management of encryption keys, redaction of
application layer data, and masking of sensitive production data for use in
nonproduction environments for testing and development purposes.



Auditing/Monitoring
-------------------

All subcomponents produces logs and audit trails. Filebeat/Logstash
automatically collects all log files and their data are imported into Elastic
Search (ELK-stack). The presentation tool used to present the logs is "Kibana".

Automated monitoring of security and performance incidents to detect anomalous
activity or behaviour including an automated escalation process including
blocking of users or subcomponent if threat or odd behaviour is detected.

The Ceph cluster monitor looks like this

.. figure::  images/grafana.png
   :align:   center

An example audit log

.. figure::  images/kibana.png
   :align:   center


Open source components
======================
* :ref:`Components_of_Communication`
* :ref:`Ansible`
* :ref:`Ceph`
* :ref:`Zookeeper`
* :ref:`Kafka`
* :ref:`Filebeat`
* :ref:`Logstash`
* :ref:`Elasticsearch`
* :ref:`Kibana`
* :ref:`PostgreSQL`
* :ref:`Pgpool_II`
* :ref:`Jmeter`
* :ref:`Selenium`


Overview, by design
===================
* :ref:`Security`
* :ref:`Modularity`
* :ref:`Fault-tolerance`

.. toctree::
   :maxdepth: 2


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`





