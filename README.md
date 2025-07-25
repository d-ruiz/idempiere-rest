
# iDempiere Rest API

You can find the documentation on how to use it here: https://bxservice.github.io/idempiere-rest-docs/.

## Projects:
* com.trekglobal.idempiere.extensions.parent - parent pom project
* com.trekglobal.idempiere.rest.api - rest api project
* com.trekglobal.idempiere.extensions.p2 - project to build p2 repository
* iDempiere version - Current Default 12

## Folder layout:
* idempiere
* idempiere-rest
  * com.trekglobal.idempiere.extensions.parent
  * com.trekglobal.idempiere.rest.api
  * com.trekglobal.idempiere.extensions.p2

## Rest Resources
* api/v1/auth - authentication and jwt token
* api/v1/models - working with PO and attachments
* api/v1/windows - working with windows and tabs
* api/v1/forms - working with forms
* api/v1/processes - working with process and reports
* api/v1/files - to access files created by api/v1/processes
* api/v1/reference - get information about reference and lists
* api/v1/caches - get caches info, reset cache
* api/v1/nodes - get nodes info, get log files, reset and rotate logs
* api/v1/servers - servers and schedulers resource
* api/v1/infos - info windows
* api/v1/workflow - get workflow nodes, approve, reject, forward, acknowledge, setuserchoice

## Testing
* postman/trekglobal-idempiere-rest.postman_collection.json
  * must run "POST api/v1/auth/tokens" and "PUT api/v1/auth/tokens" before you can test other calls. the security token created by the 2 calls is valid for 1 hour.

## p2 deployment
* at idempiere-rest, run mvn verify 
* copy update-rest-extensions.sh to your idempiere instance's root folder
* at your idempiere instance's root folder (for instance, /opt/idempiere), run ./update-rest-extensions.sh <file or url path to com.trekglobal.idempiere.extensions.p2/target/repository>
* for e.g, if your source is at /ws/idempiere-rest, ./update-rest-extensions.sh file:////ws/idempiere-rest/com.trekglobal.idempiere.extensions.p2/target/repository
* if the bundle doesn't auto start after deployment (with STARTING status), at osgi console, run "sta com.trekglobal.idempiere.rest.api" to activate the plugin
