.. _Solution_overview:

SduCloud
========
Link:
https://cloud.sdu.dk



Introduction
------------

SduCloud have been designed and programmed at the eScience Center at the University Of Southern Denmark.

The 3. party components that are being used are provided by the open source community.

The functionality follows the requirements from the NSAS description.

Scaleability have has a high priority in the design specification of the solution. This target have been reached by implementing all the "moving parts"
as micro services and a event based messaging system(Kafka).



Application Overview
====================

* :ref:`screens/screens_main.rst`



Security
--------

To secure that SduCloud is GDPR compliance following design patterns have been implemented :

Access Controls
---------------

Wayf

Privileged users are proxy users so all none system users are granted the least privilege.

All duties within the system are handled by services

All transactions are authenticated by Json Web Tokens https://jwt.io/ (JSR7519) which is granted to each user session as part of the authorisation process.

Certificates
------------


Dataprotection
--------------

Encryption for data at rest and in motion

prevent unauthorized access, it is transparent to applications and users, it provides a strong preventive control, and modern solutions typically experience low performance impact. Additional data protection technologies include management of encryption keys, redaction of application layer data, and masking of sensitive production data for use in nonproduction environments for testing and development purposes.



Auditing/Monitoring
-------------------

All subcomponents produces logs and audit trails.

Automated monitoring of security and performance incidents to detect anomalous activity or behaviour.

Automated escalation process including blocking of users or subcomponent if threat or odd behaviour is detected.

