.. _Confluent_Platform:

Confluent Platform
===================
Confluent Platform is an Apache Kafka-based streaming platform. It simplifies connecting data sources to Kafka, building applications with Kafka, as well as securing, monitoring, and managing our Kafka infrastructure.

.. note::
   
   For more information on Confluent Platform, please refer to `<https://docs.confluent.io/current/platform.html>`_


Confluent Installation
------------------------
* Playbook: confluent.yml

* Role: confluent

* Version and Dependencies

 * Open Source 3.3.1 (Java 1.7 or later)

.. note::
   
   For more information on our Confluent Platform installation and configuration, please refer to
   `<https://github.com/SDU-eScience/Ansible/blob/master/confluent.yml>`_
   `<https://github.com/SDU-eScience/Ansible/tree/master/roles/confluent>`_


.. _Kafka:

Kafka
------
Kafka is a distributed streaming platform. We use Kafka to build and process our streaming data pipeline. It allow us to

* Publish and subscribe to streams of records.
* Store streams of records in a fault-tolerant way.
* Process streams of records as they occur.

Kafka Streams
^^^^^^^^^^^^^
Kafka Streams is a client library for building applications and microservices, where the input and output data are stored in Kafka clusters. By implementing Kafka Streams API to our micro-services, we are able to build an real-time data pipeline to log users' activities, such activities as uplaoding a file, running an application and starting a job against HPCs.

.. note::

  For more information on Kafka Streams, please refer to `<https://kafka.apache.org/documentation/streams/>`_ 

.. _Zookeeper:

Zookeeper
---------
Zookeeper is a centralized service for maintaining configuration information, naming, providing distributed synchronization, and providing group services. Our application is implemented by lots of micro-services, all the mircro-services are designed in a way that they can be discovered, monitored and configured seamlessly. Therefore, we use Zookeeper for our microservice registration and discovery.

.. note::

   For more information on Zookeeper, please refer to `<https://zookeeper.apache.org/>`_
