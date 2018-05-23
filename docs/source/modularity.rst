.. _Modularity:

Modularity
===========

Our application consists of a collection of loosely coupled microservices, helper components as well as the web frontend. The benefit of decomposing our application into different smaller services is that it improves release cycles(development,test and deployment).
(names shown below are identical to the git name in the main repository)
 
Microservices 
==============
* :ref:`Api-gateway-service`
* :ref:`App-service`
* :ref:`Auth-service`
* :ref:`Metadata-service`
* :ref:`Notification-service`
* :ref:`Storage-service`
* :ref:`Upload-service`
* :ref:`Zenodo-service`

Helper components
=================
* :ref:`Abc2-sync`
* :ref:`Client-core`
* :ref:`Service-common`

Database
========
* :ref:`Sduclouddb`

Frontend
========
* :ref:`Frontend-web`