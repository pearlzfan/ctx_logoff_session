# Synopsis
This playbook executes Powershell scripts that logs off user selected by Tower Account Admin. It uses two different methods for logging off user's session. First method stops "emuser" service running under selected user and then logoffs the session. If this solution won't work admin can select second method that kills all processes running under selected user and then logoffs the session. After executing the tasks responsible for logoff playbook shows the status in the job log:
* "User session does not exists" - this means that the script didn't find selected user's open session on the server
* "user {{ username }} session successfully logged off"

Playbook will not enable operator to enter more than one server name to prevent unwanted logoffs and mistakes.
Operator can define extra variables in the jobtemplate's survey:
* method - select one of two method to logoff the user
  1 - stop the emuser service and logoff user's session
  2 - kill user's processes and session logoff
* username - enter username for method 1: stop emuser service
* domain_user - enter domain\username for method 2: kill users processes and then logoff
