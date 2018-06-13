.. _technical-overview:

Technical Overview of SDUCloud
================================================================================

* Technical
    * Microservices and scalability
    * Ceph
    * List of open source technologies, highlight why we use them
* Security
    * Authentication (WAYF, JWT)
    * Authorization
        * Principle of least privilege
    * Encryption, in transit and at rest
        * HTTPS Only. Digicert certificates
        * Data is rest is encrypted
    * Logging and auditing
        * Enable us to trace activity for any file in the system
        * Automated monitoring of systems

SDUCloud is, at its core, a system for handling massive amounts of research
data. Because of this, **scalability** has been a key concern right from the
start. SDUCloud has been built from the ground up to avoid having scalability
issues and having **no single point-of-failure**, to minimize any potential
downtime.

The backend, which powers SDUCloud, has been designed with a microservice
architecture. A microservice architecture allows us to deliver a scalable
solution with little to no down time. The backend is built on top of
**open-source components** that follow the same philosophy.

.. figure:: images/components_of_communication.png
   :align:  center

   Overall architecture of communication in SDUCloud

We use Ceph_ as our storage back-end. Ceph is an object store that provides
distributed and scalable storage with no single point-of-failure. It has been
used by CERN to handle double digit petabytes of data [#]_.

For data discovery we use Elasticsearch_. Elasticsearch is a distributed
search and analytics engine. Like Ceph and SDUCloud built to be a highly
reliable system. Elasticsearch has been used in many large systems for
free-text search, for example, it powers the search features of Wikimedia
[#]_ [#]_.

We use Kafka_ for stream processing and it helps us enable loosely-coupled
communication between microservices. Having microservices be loosely-coupled
is what helps us achieve better scalability. Kafka has been used by various
large companies, for example, it has been used by the New York Times to store
and distribute published content [#]_.

Kafka is also used as our backbone for all logging.

.. [#] https://ceph.com/community/new-luminous-scalability/
.. [#] https://www.elastic.co/elasticon/2015/sf/navigating-through-worlds-encyclopedia
.. [#] The developers of Wikipedia_
.. [#] https://open.nytimes.com/publishing-with-apache-kafka-at-the-new-york-times-7f0e3b7d2077

.. _Ceph: https://ceph.com
.. _Elasticsearch: https://www.elastic.co/products/elasticsearch
.. _Wikipedia: https://wikipedia.org
.. _Kafka: https://kafka.apache.org

Security
--------------------------------------------------------------------------------

As part of the GDPR compliance the following design patterns have been
implemented:

Access Controls
--------------------------------------------------------------------------------

Wayf

Privileged users are proxy users so all none system users are granted the least
privilege.

All duties within the system are handled by micro services that acts on behalf
of the logged in user according to the actual permissions that have been granted
to the users role.

On the technical level all transactions (frontend/backend) are authenticated by
JSON Web Tokens https://jwt.io/ (JSR7519) which is granted to each user session
as part of the authorization process.


.. figure::  images/WAYF.png
   :align:   center


Certificates
--------------------------------------------------------------------------------
Certificates from Digicert_ have been installed on all servers.

.. _Digicert: https://www.digicert.com/


Data Protection
--------------------------------------------------------------------------------

Encryption for data at rest and in motion prevents unauthorized access, it is
transparent to applications and users, it provides a strong preventive control,
and modern solutions typically experience low performance impact. Additional
data protection technologies include management of encryption keys, redaction of
application layer data, and masking of sensitive production data for use in
non-production environments for testing and development purposes.

Auditing/Monitoring
--------------------------------------------------------------------------------

All subcomponents produces logs and audit trails. Filebeat/Logstash
automatically collects all log files and their data are imported into Elastic
Search (ELK-stack). The presentation tool used to present the logs is "Kibana".

Automated monitoring of security and performance incidents to detect anomalous
activity or behavior including an automated escalation process including
blocking of users or subcomponent if threat or odd behavior is detected.

The Ceph cluster monitor looks like this

.. figure::  images/grafana.png
   :align:   center

An example audit log

.. figure::  images/kibana.png
   :align:   center


Open source components
================================================================================

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
================================================================================

* :ref:`Security`
* :ref:`Modularity`
* :ref:`Fault-tolerance`

Indices and tables
================================================================================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
