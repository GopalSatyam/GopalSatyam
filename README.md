Unified Dashboard as name suggests is to created multiple dashboards into one. Here are each of the dashboards included as part of Unified Dashboard


Live Alerts Dashboard


Purpose of this dashboard is to display the current OCTA Monitoring alerts that are not in HARMLESS which means the application is not acting as expected.
Fields displayed in the dashboard
Client Name
Instance Name
Device Name (Asset where the job is deployed)
Alert Job ID (Job ID of the alert in Monitoring jobs for that Client Instance)
Alert Job Name (Original script name of the job deployed for monitoring)
Alert Description (Description specific to the job deployed for that Client Instance)
Alert Severity (Severity of the Alert which determines the ticket severity created in SNOW)
FATAL (Sev-1)
CRITICAL (Sev-2)
MINOR (Sev-3)
WARNING (Sev-4)
HARMLESS (Alert is cleared and ticket is auto closed)
Last Run Time (Time when the job last run on the Client Device)
Alert Count (No. of times the Alert has repeated)
View Log (View Detailed Output of the alert)


Tips : 
You can find more details about the Alert by Navigating OCTA via Main Menu > Monitoring > Monitoring Jobs > Select Client and Instance > Find your job id of the alert generated
In case you want to view the log/output details of the log you may review the log under <PSMON_BASE>/<Instance Name>/logs/<jobid>.<job name>.log
PSMON_BASE is /opt/psmon on unix systems
PSMON_BASE is C:\psmon on windows systems
You can check the list of alerts generated today onon a specific server by viewing the file on server at location <PSMON_BASE>/daemon/psmon.<date>
PSMON_BASE is /opt/psmon on unix systems
PSMON_BASE is C:\psmon on windows systems


Preprod Alerts Dashboard


Purpose of this dashboard is to display the current OCTA Monitoring alerts that are not in HARMLESS which means the application is not acting as expected (For Clients which are not yet live)
Fields displayed in the dashboard
Client Name
Instance Name
Device Name (Asset where the job is deployed)
Alert Job ID (Job ID of the alert in Monitoring jobs for that Client Instance)
Alert Job Name (Original script name of the job deployed for monitoring)
Alert Description (Description specific to the job deployed for that Client Instance)
Alert Severity (Severity of the Alert which determines the ticket severity created in SNOW)
FATAL (Sev-1)
CRITICAL (Sev-2)
MINOR (Sev-3)
WARNING (Sev-4)
HARMLESS (Alert is cleared and ticket is auto closed)
Last Run Time (Time when the job last run on the Client Device)
Alert Count (No. of times the Alert has repeated)
View Log (View Detailed Output of the alert)


Tips : 
You can find more details about the Alert by Navigating OCTA via Main Menu > Monitoring > Monitoring Jobs > Select Client and Instance > Find your job id of the alert generated
In case you want to view the log/output details of the log you may review the log under <PSMON_BASE>/<Instance Name>/logs/<jobid>.<job name>.log
PSMON_BASE is /opt/psmon on unix systems
PSMON_BASE is C:\psmon on windows systems
You can check the list of alerts generated today onon a specific server by viewing the file on server at location <PSMON_BASE>/daemon/psmon.<date>
PSMON_BASE is /opt/psmon on unix systems
PSMON_BASE is C:\psmon on windows systems


HBAUDIT Dashboard


Purpose of this dashboard is to display the Heartbeat Alerts of Servers running PSMON agent which are not reporting any heartbeat back to OCTA server. There are multiple issues this could be causing this as outlined here
Server is not responsive - Reach out to Platform team to confirm there are issues with the server accessibility, in case required go for a Sev to restore the server to normal state through by engaging the TRM team
psmon Agent is hung - kill any psmon agents using the following methods
First step is to kill the psmon agent
Run command pkill -u octagent on unix servers
Open Task Scheduler and kill any tasks with title psmon_win.pl in Windows servers
Remove psmon daemon lock file
/opt/psmon/daemon/psmon.pid on unix servers
C:\psmon\daemon\psmon.pid on Windows servers
The psmon agent is already in crontab or schtasks, so it should restart automatically after the above steps are done and hbaudit alert should be gone soon
octagent password expired - Login as root to the target server and su - octagent, if you see the prompt ask you to change password for octagent as the password expired. Come back as root and run the command passwd octagent to set the new password for octagent user. This should take care of the issue.
Reach out to OCTA team on slack at #sq-psft-chpt-octa to check on issue further


FileSystem Alerts Dashboard


Purpose of this dashboard is to review the current Filesystem usage alerts from all servers which have psmon agent with a current FileSystem usage greater than or equal to 95%. Action to be taken to resolve issues
Engage appropriate team to clear some files or data to free up space on the specific FileSystem
Engage Platform team with requisite approvals to add space to the FileSystem. Ensure TSD is updated post the upgrade of FileSystem size
If the FileSystem is not in our control and we cannot further increase the size, then you can suppress the alarms on this file system by navigating in OCTA to Main Menu > Maintenance > FileSystem Maintenance > Add New. This will suppress the alarms on that specific FileSystem Mount on the specific server


FileSystem Mounts Dashboard


Purpose of this dashboard is to review the current Filesystem mount alerts from all servers which have psmon agent with a current FileSystem and those file system mounts are not reported back to OCTA as still existing or are not in Read-Write mode. Action to be taken to resolve issues
Engage CTL team to look at why the filesystem does not exist or not in RW mode on the server
In case of client server filesystem, ensure Network is not broken between IBM and Client network, Engage TRM if necessary
If the FileSystem is no longer needed, then you can suppress the alarms on this file system by navigating in OCTA to Main Menu > Maintenance > FileSystem Maintenance > Add New. This will suppress the alarms on that specific FileSystem Mount on the specific server
In case that File System Mount is no longer in use, reach out to OCTA team on slack channel #sq-psft-chpt-octa to permanently remove the file system from monitoring

