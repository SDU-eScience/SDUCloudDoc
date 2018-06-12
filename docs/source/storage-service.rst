.. _Storage-service:

Storage Service
================================================================================

Version
--------------------------------------------------------------------------------

0.4.0

Description
--------------------------------------------------------------------------------

This service handles all file system events.

Service Dependencies
--------------------------------------------------------------------------------

This microservice has the following internal dependencies:

* :ref:`auth-service`
* :ref:`notification-service`
* :ref:`service-common`

Service Interoperability
--------------------------------------------------------------------------------

The following is a non-exhaustive list of internal services which use this
microservice:

* :ref:`app-service`
* :ref:`frontend-web`
* :ref:`metadata-service`
* :ref:`zenodo-service`

Tests
--------------------------------------------------------------------------------

.. TODO Replace this with a link to CI test report

- Controllers
	- Files
		- Annotate Files:	
			- Annotate file as Admin
			- Annotate file as User
			- Annotate file with illegal annotation
			- Annotate file with illegal path
		- Copy Files:
			- Make a copy of a file
			- Make a copy from a non-existing path
			- Make a copy of a file to an already existing directory path
		- Create Directories:
			- Create a directory with correct input
			- Create a directory in home
			- Create a directory in non exisiting directory
			- Create a directory that already exist
		- Delete:
			- Delete a folder
			- Delete a file
		- Favorites:
			- Make a folder favorite and delete it
			- make a file favorite and delete it
		- ls
			- List at correct path
			- List at incorrect path
			- List without Authentication
		- Make Open Access
			- Mark file as open access
		- Move
			- Move file
			- Move to same destination
			- Move to non existing destination
			- Move nonexisting file
			- Move file and rename
		- Stat
			- Stat file
			- Stat non exisiting path
		- Sync Files
			- Sync folder path
	- Share
		- Create, List and Accept
		- Create when not owner of file
		- Create when path is nonexisting
		- Create, List and revoke
		- Create, List and reject
		- Create, List and Update
		- Create, List and Update on not own file
	- Download
		- Download File
		- Download Folder
		- Donload from non exisiting path
		- Download Files Bulk
		- Download Files Bulk with missing files
- Service code
	- Bulk Download
		- Make a bulk download
		- Make a bulk download with missing files
	- Bulk Upload
		- From dir to file
		- From file to dir
		- Standard upload
		- Overwrite
		- Reject
		- Rename
		- Shell Injection
	- Checksum
		- Generate checksum using SHA1
		- Generate checksum with illegal algorithm
	- Copy
		- Standard copy
	- Favorites
		- Create favorite
		- Remove favorite
	- FileSystem
		- Output parsing
		- Favorites in wrong format
		- Type is not D,F or L
		- Favorites
	- Make
		- Sanitize of path
		- New dir already exists
	- Move
		- Move directory
		- Move file
		- Move to same location
		- Move to nonexisiting location
	- Remove
		- Remove file
		- Remove nonexisting
	- Share
		- Grant Share with low level failure
		- Grant share with missing permission
		- Share Grant
		- Revoke Grant
	- XAttr
		- Basic passing