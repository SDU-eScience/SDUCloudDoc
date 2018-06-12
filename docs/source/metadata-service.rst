.. _Metadata-service:

Metadata-service
================

Version
-------

1.0

Description
-----------

The metadata-service makes it possible to add metadata to a project or data object. The metadata is stored in Elasticsearch. The metadata is searchable from within the user interface.

Service dependencies
------------------------

* :ref:`Auth-service`
* :ref:`Service-common`
* :ref:`Storage-service`

Service interoperability
------------------------

* :ref:`Frontend-web`

Tests
------------------------
- Controllers
	- Metadata
		- SimpleQuery
		- Find By Path (No Project)
		- Find By ID fail
		- Find By Path
		- Find By ID
		- Update metadata
	- Project
		- Create and get project
		- Crate and try to get not own project
		- Create project with wrong path
		- Create project but with annotation error
		- Create existing project
		- Get non existing project