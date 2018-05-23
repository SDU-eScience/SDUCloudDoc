.. _Modularity:

Modularity
===========

Our application backend is structured by a collection of loosely coupled microservices. The benefit of decomposing our application into different smaller services is that it improves release cycles(development,test and deployment).
(module names shown below are identical to the git name)
 
Backend modules
* abc2-sync
* client-core
* service-common
* api-gateway-service
* app-service
* auth-service
* metadata-service
* notification-service
* storage-service 
* upload-service
* zenodo-service

Frontend
* :ref:`Frontend-web`