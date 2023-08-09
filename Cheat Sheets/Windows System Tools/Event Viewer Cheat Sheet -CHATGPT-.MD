------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# PS : ChatGPT makes mistakes, consider "trust but verify" principle
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#Events to Monitor
https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/appendix-l--events-to-monitor
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#run 
eventvwr.msc            Event viewer
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Event Viewer(Local)-Windows Logs (shutdown / restart )

#In order to find out what user stopped the Windows Event Log, you can use the following PowerShell commands, ChatGPT
PS HKLM:\> Stop-Service -Name "eventlog" -Force
PS HKLM:\> Start-Service -Name "eventlog"

PS HKLM:\> Get-WinEvent -FilterHashtable @{LogName='Security'; ID=1100} -MaxEvents 50

   ProviderName: Microsoft-Windows-Eventlog

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
2/18/2023 2:35:13 AM          1100 Information      The event logging service has shut down.
2/18/2023 1:41:43 AM          1100 Information      The event logging service has shut down.
2/15/2023 9:59:07 AM          1100 Information      The event logging service has shut down.
2/10/2023 8:04:13 AM          1100 Information      The event logging service has shut down.
2/9/2023 11:43:27 PM          1100 Information      The event logging service has shut down.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#ChatGPT 

Chainsaw is a powerful log viewer tool that can be used for Windows event investigations. It is an open-source software developed by Apache and can be downloaded for free. Chainsaw can help you quickly and efficiently analyze Windows event logs, identify patterns, and troubleshoot issues. Here are the steps to use Chainsaw for Windows event investigations:

    Download and install Chainsaw: First, you need to download the latest version of Chainsaw from the Apache website and install it on your computer.

    Export the Windows event logs: Next, you need to export the Windows event logs from the target machine. To do this, open the Event Viewer on the target machine, select the event logs you want to export, right-click, and select "Save All Events As." Choose the file type as "evt" or "evtx" and save the file to a location accessible from your computer.

    Import the Windows event logs into Chainsaw: Launch Chainsaw and go to File > Load Log4j/Logback Logs. Select the exported Windows event log file and click "Open." The Windows event logs will now be displayed in Chainsaw.

    Filter the Windows event logs: Chainsaw provides a powerful filtering mechanism that allows you to quickly identify specific events of interest. To filter the Windows event logs, go to the "Filter" tab in Chainsaw and define the filter criteria based on the event ID, source, severity, or any other attribute of the Windows event logs.

    Analyze the Windows event logs: Once the logs are filtered, you can analyze them to identify patterns or troubleshoot issues. Chainsaw provides several features that can help you in this regard, such as sorting the logs based on various attributes, grouping similar events together, or highlighting events that match specific criteria.

    Export the results: Once you have analyzed the logs, you may need to export the results for further investigation or reporting. Chainsaw provides several export options, such as exporting the filtered logs to a CSV file or exporting the entire log session to a file.

In summary, Chainsaw is a powerful tool that can help you quickly and efficiently analyze Windows event logs. By following the steps outlined above, you can use Chainsaw to filter, analyze, and export the logs to troubleshoot issues, identify patterns, and improve the overall security of your Windows environment
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#ChatGPT 

Sure, here are a few examples of how to use Chainsaw to troubleshoot issues in a Windows environment:

    Identifying Windows service failures: When a Windows service fails, it can be challenging to identify the root cause. Chainsaw can help you quickly identify the service failure by filtering the Windows event logs based on the service name and event ID. For example, you can filter the logs for event ID 7031, which indicates that a service has stopped unexpectedly, and then look for the corresponding service name in the logs. Once you have identified the service, you can investigate further to identify the cause of the failure, such as a configuration issue or a dependency problem.

    Analyzing user login issues: When users have trouble logging in to a Windows environment, it can be helpful to analyze the Windows event logs to identify any error messages or authentication failures. Chainsaw can help you quickly filter the logs for failed login attempts or other login-related events. For example, you can filter the logs for event ID 4625, which indicates a failed login attempt, and then look for the corresponding username or IP address in the logs. Once you have identified the source of the login issue, you can investigate further to identify the root cause, such as a password mismatch or a network connectivity problem.

    Troubleshooting network connectivity issues: When network connectivity issues occur in a Windows environment, it can be challenging to identify the source of the problem. Chainsaw can help you quickly filter the Windows event logs for network-related events, such as DNS lookup failures or TCP/IP connection failures. For example, you can filter the logs for event ID 1101, which indicates a DNS lookup failure, and then look for the corresponding hostname or IP address in the logs. Once you have identified the network-related event, you can investigate further to identify the cause of the problem, such as a misconfigured DNS server or a firewall blocking traffic.

    Investigating security-related events: Security-related events can be critical to investigate to ensure the security of a Windows environment. Chainsaw can help you filter the logs for security-related events, such as failed login attempts or malware detection events. For example, you can filter the logs for event ID 4625, which indicates a failed login attempt, and then look for the corresponding username or IP address in the logs. Once you have identified the security-related event, you can investigate further to identify the cause of the problem, such as an attempted brute-force attack or a compromised user account.

In summary, Chainsaw can be a powerful tool to troubleshoot issues in a Windows environment by allowing you to quickly filter and analyze the Windows event logs. By using Chainsaw to investigate specific use cases, such as identifying service failures, analyzing login issues, troubleshooting network connectivity, or investigating security-related events, you can improve the overall security and stability of your Windows environment.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#ChatGPT

Sure, I can explain how to convert an EVTX file into a CSV file in Excel.

An EVTX file is a Windows event log file, and Excel does not support importing EVTX files directly. However, you can use the "Event Viewer" tool in Windows to export the EVTX file as a CSV file, which can then be opened and edited in Excel.

Here are the steps to convert an EVTX file to a CSV file using Event Viewer and Excel:

    Open Event Viewer: Click on the Windows Start button and type "Event Viewer" in the search box. Click on the "Event Viewer" app to launch it.

    Export the EVTX file: In the Event Viewer, select the log file you want to export (e.g., "Application" or "Security"), and then click "Action" from the menu bar. Select "Export Log" and choose a location to save the exported file. In the "Save as type" drop-down list, select "CSV (Comma delimited)" and give the file a name.

    Open the CSV file in Excel: Open Excel and go to the "Data" tab. Click on "From Text/CSV" and select the CSV file you exported from Event Viewer. Follow the prompts to import the file into Excel. Make sure to select the appropriate delimiter (comma) in the import wizard.

    Convert the data into a table: Once the data is imported into Excel, select the entire table (Ctrl + A) and click on the "Format as Table" button in the "Styles" section of the "Home" tab. Choose a table style that you prefer.

    Edit and analyze the data: The converted CSV data is now ready for editing and analysis in Excel. You can sort, filter, and analyze the data using Excel's built-in tools.

That's it! By following these steps, you can easily convert an EVTX file into a CSV file and open it in Excel for further analysis.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#ChatGPT

Sure, as a Windows forensics analyzer, I can explain how to create event baselines with the COUNTIF function in Excel when investigating security-related events on Windows 10.

Creating event baselines can help you identify changes in the Windows event logs over time and detect potential security incidents. To create an event baseline with the COUNTIF function in Excel, follow these steps:

    Export the Windows event logs: First, you need to export the Windows event logs from the target machine. To do this, open the Event Viewer on the target machine, select the event logs you want to export, right-click, and select "Save All Events As." Choose the file type as "evt" or "evtx" and save the file to a location accessible from your computer.

    Import the Windows event logs into Excel: Launch Excel and go to the "Data" tab. Click on "From Text/CSV" and select the exported Windows event log file. Follow the prompts to import the Windows event logs into Excel.

    Filter the Windows event logs: Once the logs are imported, filter the logs for the specific event IDs or event sources that you want to create a baseline for. For example, you can filter the logs for event ID 4624, which indicates a successful login event.

    Use the COUNTIF function: After filtering the logs, you can use the COUNTIF function in Excel to count the number of occurrences of each event ID or event source. To use the COUNTIF function, select a cell where you want to display the count, then enter the formula "=COUNTIF(range, criteria)." In the "range" field, select the filtered event log column that contains the event IDs or event sources. In the "criteria" field, enter the specific event ID or event source that you want to count. For example, to count the number of successful login events (event ID 4624), you can enter "=COUNTIF(A:A,4624)" in a cell.

    Create a baseline chart: Once you have calculated the counts for each event ID or event source, you can create a baseline chart in Excel to visualize the changes over time. To create a chart, select the cells with the counts, then go to the "Insert" tab and select the chart type that you want to use. For example, you can use a line chart to show the trend of the counts over time.

    Analyze the baseline chart: After creating the baseline chart, you can use it to identify any changes in the Windows event logs over time. For example, if you notice a sudden spike in the number of failed login events, it may indicate a potential security incident that needs further investigation.

In summary, using the COUNTIF function in Excel can help you create event baselines and identify potential security incidents in Windows event logs. By following the steps outlined above, you can filter the logs, use the COUNTIF function to count the occurrences of specific events, create a baseline chart, and analyze the chart to detect any changes over time.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#Windows Logs > System, ChatGPT 

Event ID 1030 #logged when the Group Policy settings cannot be read,when the Group Policy object (GPO) is corrupted, or when the computer is unable to access the domain controller
Event ID 1058 #occurs when the computer is unable to access the Sysvol share, which stores the Group Policy templates and scripts
Event ID 1704 #This event indicates that the GPO was successfully applied to the client computer
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#ChatGPT

In the Event Viewer window that opens, navigate to the "Windows Logs" folder on the left-hand side, and select the "System" log.
Look for events with the "Event ID 7036" which indicates that a service has entered the running or stopped state.
Look for events with the "Event ID 7009" which indicates that a service timeout has occurred.
Look for events with the "Event ID 7011" which indicates that a service did not respond within the specified time.
Look for events with the "Event ID 7024" which indicates that the service terminated with service-specific error.
Look for events with the "Event ID 7023" which indicates that the service terminated with the following error: The service terminated with the following service-specific error: Incorrect function.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Event ID 41  : The system has rebooted without cleanly shutting down first.
Event ID 44,43,19,20  : any anti-malware software is installed,any anti-malware software is installed
Event ID 1074: The system has been shutdown properly by a user or process. "The process X has initiated the restart / shutdown of computer on behalf of user Y for the following reason: Z." Indicates that an application or a user initiated a restart or shutdown.
Event ID 1076: "The reason supplied by user X for the last unexpected shutdown of this computer is: Y." Records when the first user with shutdown privileges logs on to the computer after an unexpected restart or shutdown and supplies a reason for the occurrence.Follows after Event ID 6008 and means that the first user with shutdown privileges logged on to the server after an unexpected restart or shutdown and specified the cause.
Event ID 6005: “The event log service was started.” Indicates the system startup.
Event ID 6006: “The event log service was stopped.” Indicates the proper system shutdown.
Event ID 6008: "The previous system shutdown was unexpected." The previous system shutdown was unexpected.
Event ID 6009: Indicates the Windows product name, version, build number, service pack number, and operating system type detected at boot time.
Event ID 6013: Displays the uptime of the computer.The system uptime in seconds.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Event Viewer(Domain Controller)-Windows Logs-Security
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
1100 	The event logging service has shut down
1101 	Audit events have been dropped by the transport.
1102 	The audit log was cleared
1104 	The security Log is now full
1105 	Event log automatic backup
1108 	The event logging service encountered an error
4608 	Windows is starting up
4609 	Windows is shutting down
4610 	An authentication package has been loaded by the Local Security Authority
4611 	A trusted logon process has been registered with the Local Security Authority
4612 	Internal resources allocated for the queuing of audit messages have been exhausted, leading to the loss of some audits.
4614 	A notification package has been loaded by the Security Account Manager.
4615 	Invalid use of LPC port
4616 	The system time was changed.
4618 	A monitored security event pattern has occurred
4621 	Administrator recovered system from CrashOnAuditFail
4622 	A security package has been loaded by the Local Security Authority.

==========================================================================================================
#detect abnormal and possibly  unauthorized insider activity, like a logon from an inactive or restricted account, users logging on outside of normal working hours, concurrent  logons to many resources
4624 # target computer not a domain member,(Successfull logon),An account was successfully logged on

==========================================================================================================
#ChatGPT

Event ID 4624 is a security event that gets generated in the Microsoft Windows event log every time a user successfully logs on to a computer or server. The event provides important details about the user's logon, such as the user account name, logon type, and logon timestamp.

Logon types are numeric codes that indicate the type of logon that was performed. There are several different logon types, including:

    Interactive (logon at the console of the computer)
    Network (logon via a network connection)
    Batch (logon via a scheduled task)
    Service (logon via a Windows service)
    RemoteInteractive (logon via a Remote Desktop or Terminal Services session)
    CachedInteractive (logon using cached credentials)

The logon type is specified in the event's Logon Type field. Knowing the logon type can help you understand how the user logged on and what resources they may have accessed during their session.

For example, if the logon type is 2, it indicates that the user logged on via a network connection, which could mean that they accessed a network share or used a remote desktop connection. If the logon type is 3, it indicates that the user logged on by means of a batch job or scheduled task.

By reviewing the Event ID 4624 log entries, system administrators can monitor and track user activity on their networks, including identifying suspicious or unauthorized access attempts.
==========================================================================================================
#ChatGPT

In the Microsoft Windows event log, logon types are numeric codes that indicate the type of logon that was performed. These logon types can help system administrators and security professionals to understand how users are accessing a system and to identify potential security issues.

Here are the different logon types and their corresponding numeric codes:

    Interactive (logon at keyboard and screen): This logon type occurs when a user logs on to a system interactively, by typing their username and password at the keyboard. This logon type is assigned the numeric code 2.

    Network (i.e. connection to shared folder on this computer from elsewhere on network or IIS logon): This logon type occurs when a user accesses resources on a remote system over the network, such as connecting to a shared folder or accessing a web application using IIS. This logon type is assigned the numeric code 3.

    Batch (i.e. scheduled task): This logon type occurs when a scheduled task is executed. This logon type is assigned the numeric code 4.

    Service (Service startup): This logon type occurs when a service is started. This logon type is assigned the numeric code 5.

    RemoteInteractive (Terminal Services, Remote Desktop or Remote Assistance): This logon type occurs when a user connects to a system remotely using a remote desktop or terminal services client. This logon type is assigned the numeric code 10.

    CachedInteractive (logon with cached domain credentials): This logon type occurs when a user logs on to a system using cached domain credentials. This logon type is assigned the numeric code 11.

Understanding the different logon types and their corresponding numeric codes can be useful for monitoring system access, troubleshooting issues, and identifying potential security threats.
==========================================================================================================
#ChatGPT

In Windows Server logs, the Logon Type field indicates the type of logon that was used when a user or a computer logged on to the system. The Logon Type values are defined as follows:

    0: System logon (generated by the system when it starts)
    2: Interactive logon (when a user logs on at the console or through a remote desktop session)
    3: Network logon (when a user logs on to the system over the network)
    4: Batch logon (when a batch job runs on the system)
    5: Service logon (when a service starts and logs on to the system)
    6: Proxy logon (when a service logs on using a proxy account)
    7: Unlock logon (generated when a workstation is unlocked)
    8: Network clear text logon (when a user logs on over the network using clear text authentication)
    9: New credentials logon (when a user reuses an existing token to log on with new credentials)
    10: Remote interactive logon (when a user logs on remotely using Remote Desktop Services)

The logon types are used by Windows to record and track logon activity on the system. They can help administrators to identify the source of logon events and to detect potential security breaches, such as unauthorized logon attempts.

The logon types are also used by some security tools and solutions, such as SIEMs and log management platforms, to analyze and correlate logon events with other security-related events on the system, such as privilege escalation, file access, and network traffic. By understanding the relationships between logon types and other security events, administrators can gain a better understanding of the security posture of their systems and take appropriate actions to protect them from threats.
==========================================================================================================
#ChatGPT

Interactive logon is a logon type in Windows Server logs that indicates when a user logs on to the system at the console or through a remote desktop session. In other words, it refers to the process of logging on to a system by physically or remotely interacting with it.

When a user logs on interactively, they typically provide their username and password to the system. The system then authenticates the user's credentials and creates a new session for the user, which provides access to resources and services on the system.

Interactive logon can occur at the console of the system, which is the physical device that hosts the operating system, or through a remote desktop session, which allows users to connect to the system over a network and interact with it as if they were sitting in front of the console. Remote desktop sessions are typically used for remote administration, remote access to applications, or telecommuting.

Interactive logon is an important logon type to track and monitor in Windows Server logs, as it can indicate when users are accessing the system and what resources and services they are accessing. By analyzing interactive logon events, administrators can identify potential security risks, such as unauthorized access attempts, failed logon attempts, or suspicious activity. They can also use interactive logon events to troubleshoot issues related to user access and session management on the system.

==========================================================================================================
#ChatGPT

The difference between a remote desktop session and Remote Desktop Services (RDS) with respect to the logon types "Interactive logon" and "Remote interactive logon" is as follows:

    Interactive logon: This logon type refers to the process of logging on to a system by physically or remotely interacting with it. When a user logs on interactively, they typically provide their username and password to the system, and a new session is created for them. This type of logon can occur at the console of the system or through a remote desktop session.

    Remote interactive logon: This logon type specifically refers to the process of logging on remotely to a system using Remote Desktop Services (RDS). RDS is a role service in Windows Server that enables users to remotely access Windows-based desktops, applications, and data over a network connection. When a user logs on remotely using RDS, they typically connect to a server that hosts the RDS role service, provide their credentials, and a new session is created for them on the server.

So, the key difference between a remote desktop session and RDS is that the former refers to the general process of accessing a system remotely, while the latter is a specific technology that enables remote access to Windows-based desktops, applications, and data. In terms of logon types, both interactive logon and remote interactive logon involve the creation of a new session for the user, but the latter specifically requires the use of RDS technology to establish the remote connection.

It's worth noting that Remote Desktop Services includes additional logon types beyond Remote interactive logon, such as Remote Desktop Services: Session logon and Remote Desktop Services: Console logon, which are used to differentiate between different types of remote sessions established through RDS.
==========================================================================================================
#ChatGPT

You can filter security events with ID 4624 that include logon type 10 using Computer Management as follows:

    Open Computer Management: Press Windows key + X, and then click on Computer Management.
    In the console tree, expand "Event Viewer" and then expand "Windows Logs".
    Right-click on "Security" and select "Filter Current Log".
    In the "Filter Current Log" dialog box, click on the "XML" tab.
    In the "XML" tab, check the box for "Edit query manually" and paste the following XML query into the text box:

mathematica

<QueryList>
  <Query Id="0" Path="Security">
    <Select Path="Security">
      *[System[(EventID=4624)]] and
      *[EventData[Data[@Name='LogonType']='10']]
    </Select>
  </Query>
</QueryList>

    Click on "OK" to apply the filter. The Security log will now display only events that match the filter criteria.

Note: The XML query used in this example filters for events with ID 4624 and logon type 10. You can modify the query to filter for different criteria as needed.
==========================================================================================================
#ChatGPT

To filter security events with ID 4624 that include logon type 10 and account name David using Computer Management, you can follow these steps:

<QueryList>
  <Query Id="0" Path="Security">
    <Select Path="Security">
      *[System[(EventID=4624)]] and
      *[EventData[Data[@Name='LogonType']='10'] and Data[@Name='TargetUserName']='David']
    </Select>
  </Query>
</QueryList>

==========================================================================================================
#ChatGPT

 <QueryList>
   <Query Id="0" Path="Security">
     <Select Path="Security">
       *[System[(EventID=4624)]]
       and
       *[EventData[Data[@Name='TargetUserName'] and (Data='David')]]
       and
       *[EventData[Data[@Name='LogonType'] and (Data='10')]]
     </Select>
   </Query>
 </QueryList>

==========================================================================================================
#detect possible brute-force, dictionary, and other password guess attacks, which are characterized by a sudden spike in failed logons
4625 # target computer not a domain member,(Failed logon) An account failed to log on

4626 	User/Device claims information
4627 	Group membership information.
4634 	An account was logged off
4646 	IKE DoS-prevention mode started
4647 	User initiated logoff
4648 	A logon was attempted using explicit credentials,Remote Access
4649 	A replay attack was detected
4650 	An IPsec Main Mode security association was established
4651 	An IPsec Main Mode security association was established
4652 	An IPsec Main Mode negotiation failed
4653 	An IPsec Main Mode negotiation failed
4654 	An IPsec Quick Mode negotiation failed
4655 	An IPsec Main Mode security association ended
4656 	A handle to an object was requested
4657 	A registry value was modified
4658 	The handle to an object was closed
4659 	A handle to an object was requested with intent to delete
4660 	An object was deleted
4661 	A handle to an object was requested
4662 	An operation was performed on an object
4663 	An attempt was made to access an object
4664 	An attempt was made to create a hard link
4665 	An attempt was made to create an application client context.
4666 	An application attempted an operation
4667 	An application client context was deleted
4668 	An application was initialized

#Attackers often elevate privileges and change permissions to perform ransomware attacks or move laterally
#enable the object's audit policy, especially for "Write DAC"/"Change Permissions" or "Take Ownership" permissions
4670 	Permissions on an object were changed,A user changing an object’s access control list triggers,Tracking who (or what) takes ownership

4671 	An application attempted to access a blocked ordinal through the TBS

#a possible pass-the-hash or other elevation of privilege attacks, such as using a tool like Mimikatz,Combined with event 4624, which shows a user has logged into an account
4672 	Special privileges assigned to new logon 

4673 	A privileged service was called
4674 	An operation was attempted on a privileged object
4675 	SIDs were filtered
4688 	A new process has been created
4689 	A process has exited
4690 	An attempt was made to duplicate a handle to an object
4691 	Indirect access to an object was requested
4692 	Backup of data protection master key was attempted
4693 	Recovery of data protection master key was attempted
4694 	Protection of auditable protected data was attempted
4695 	Unprotection of auditable protected data was attempted
4696 	A primary token was assigned to process
4697 	A service was installed in the system
4698 	A scheduled task was created
4699 	A scheduled task was deleted
4700 	A scheduled task was enabled
4701 	A scheduled task was disabled
4702 	A scheduled task was updated
4703 	A token right was adjusted
4704 	A user right was assigned
4705 	A user right was removed
4706 	A new trust was created to a domain
4707 	A trust to a domain was removed
4709 	IPsec Services was started
4710 	IPsec Services was disabled
4711 	PAStore Engine (1%)
4712 	IPsec Services encountered a potentially serious failure
4713 	Kerberos policy was changed
4714 	Encrypted data recovery policy was changed
4715 	The audit policy (SACL) on an object was changed
4716 	Trusted domain information was modified
4717 	System security access was granted to an account
4718 	System security access was removed from an account
4719 	System audit policy was changed
4720 	A user account was created
4722 	A user account was enabled
4723 	An attempt was made to change an account's password
4724 	An attempt was made to reset an accounts password
4725 	A user account was disabled
4726 	A user account was deleted
4727 	A security-enabled global group was created
4728 	A member was added to a security-enabled global group
4729 	A member was removed from a security-enabled global group
4730 	A security-enabled global group was deleted
4731 	A security-enabled local group was created
4732 	A member was added to a security-enabled local group
4733 	A member was removed from a security-enabled local group
4734 	A security-enabled local group was deleted
4735 	A security-enabled local group was changed
4737 	A security-enabled global group was changed
4738 	A user account was changed
4739 	Domain Policy was changed
4740 	A user account was locked out
4741 	A computer account was created
4742 	A computer account was changed
4743 	A computer account was deleted
4744 	A security-disabled local group was created
4745 	A security-disabled local group was changed
4746 	A member was added to a security-disabled local group
4747 	A member was removed from a security-disabled local group
4748 	A security-disabled local group was deleted
4749 	A security-disabled global group was created
4750 	A security-disabled global group was changed
4751 	A member was added to a security-disabled global group
4752 	A member was removed from a security-disabled global group
4753 	A security-disabled global group was deleted
4754 	A security-enabled universal group was created
4755 	A security-enabled universal group was changed
4756 	A member was added to a security-enabled universal group
4757 	A member was removed from a security-enabled universal group
4758 	A security-enabled universal group was deleted
4759 	A security-disabled universal group was created
4760 	A security-disabled universal group was changed
4761 	A member was added to a security-disabled universal group
4762 	A member was removed from a security-disabled universal group
4763 	A security-disabled universal group was deleted
4764 	A groups type was changed
4765 	SID History was added to an account
4766 	An attempt to add SID History to an account failed
4767 	A user account was unlocked

#Group Policy Management Console(Domain Controller)-group policy settings - Computer Configuration/Policies/WindowsSettings/Security Settings/Advanced Audit Policy Configuration/AuditPolicies/ Audit Other Account Logon Events - set to success and failure
4768 #A Kerberos authentication ticket (TGT) was requested

4769 	A Kerberos service ticket was requested
4770 	A Kerberos service ticket was renewed

#Group Policy Management Console(Domain Controller)-group policy settings - Computer Configuration/Policies/WindowsSettings/Security Settings/Advanced Audit Policy Configuration/AuditPolicies/Audit Kerberos Authentication service>set to success and failure
4771 #logon the attempt with a domain account,authentication failure,Kerberos pre-authentication failed

4772 	A Kerberos authentication ticket request failed
4773 	A Kerberos service ticket request failed
4774 	An account was mapped for logon
4775 	An account could not be mapped for logon

#Group Policy Management Console(Domain Controller)- group policy settings - Computer Configuration/Policies/WindowsSettings/Security Settings/Advanced Audit Policy Configuration/AuditPolicies/Account Logon/Audit Credential Validation- set to Failures
4776 #failed RDP connections,logon attempt with a domain account,authentication failure,The domain controller attempted to validate the credentials for an account 

4777 	The domain controller failed to validate the credentials for an account
4778 	A session was reconnected to a Window Station
4779 	A session was disconnected from a Window Station
4780 	The ACL was set on accounts which are members of administrators groups
4781 	The name of an account was changed
4782 	The password hash an account was accessed
4783 	A basic application group was created
4784 	A basic application group was changed
4785 	A member was added to a basic application group
4786 	A member was removed from a basic application group
4787 	A non-member was added to a basic application group
4788 	A non-member was removed from a basic application group..
4789 	A basic application group was deleted
4790 	An LDAP query group was created
4791 	A basic application group was changed
4792 	An LDAP query group was deleted
4793 	The Password Policy Checking API was called
4794 	An attempt was made to set the Directory Services Restore Mode administrator password
4797 	An attempt was made to query the existence of a blank password for an account
4798 	A user's local group membership was enumerated.
4799 	A security-enabled local group membership was enumerated
4800 	The workstation was locked
4801 	The workstation was unlocked
4802 	The screen saver was invoked
4803 	The screen saver was dismissed
4816 	RPC detected an integrity violation while decrypting an incoming message
4817 	Auditing settings on object were changed.
4818 	Proposed Central Access Policy does not grant the same access permissions as the current Central Access Policy
4819 	Central Access Policies on the machine have been changed
4820 	A Kerberos Ticket-granting-ticket (TGT) was denied because the device does not meet the access control restrictions
4821 	A Kerberos service ticket was denied because the user, device, or both does not meet the access control restrictions
4822 	NTLM authentication failed because the account was a member of the Protected User group
4823 	NTLM authentication failed because access control restrictions are required
4824 	Kerberos preauthentication by using DES or RC4 failed because the account was a member of the Protected User group
4825 	A user was denied the access to Remote Desktop. By default, users are allowed to connect only if they are members of the Remote Desktop Users group or Administrators group
4826 	Boot Configuration Data loaded
4830 	SID History was removed from an account
4864 	A namespace collision was detected
4865 	A trusted forest information entry was added
4866 	A trusted forest information entry was removed
4867 	A trusted forest information entry was modified
4868 	The certificate manager denied a pending certificate request
4869 	Certificate Services received a resubmitted certificate request
4870 	Certificate Services revoked a certificate
4871 	Certificate Services received a request to publish the certificate revocation list (CRL)
4872 	Certificate Services published the certificate revocation list (CRL)
4873 	A certificate request extension changed
4874 	One or more certificate request attributes changed.
4875 	Certificate Services received a request to shut down
4876 	Certificate Services backup started
4877 	Certificate Services backup completed
4878 	Certificate Services restore started
4879 	Certificate Services restore completed
4880 	Certificate Services started
4881 	Certificate Services stopped
4882 	The security permissions for Certificate Services changed
4883 	Certificate Services retrieved an archived key
4884 	Certificate Services imported a certificate into its database
4885 	The audit filter for Certificate Services changed
4886 	Certificate Services received a certificate request
4887 	Certificate Services approved a certificate request and issued a certificate
4888 	Certificate Services denied a certificate request
4889 	Certificate Services set the status of a certificate request to pending
4890 	The certificate manager settings for Certificate Services changed.
4891 	A configuration entry changed in Certificate Services
4892 	A property of Certificate Services changed
4893 	Certificate Services archived a key
4894 	Certificate Services imported and archived a key
4895 	Certificate Services published the CA certificate to Active Directory Domain Services
4896 	One or more rows have been deleted from the certificate database
4897 	Role separation enabled
4898 	Certificate Services loaded a template
4899 	A Certificate Services template was updated
4900 	Certificate Services template security was updated
4902 	The Per-user audit policy table was created
4904 	An attempt was made to register a security event source
4905 	An attempt was made to unregister a security event source
4906 	The CrashOnAuditFail value has changed
4907 	Auditing settings on object were changed
4908 	Special Groups Logon table modified
4909 	The local policy settings for the TBS were changed
4910 	The group policy settings for the TBS were changed
4911 	Resource attributes of the object were changed
4912 	Per User Audit Policy was changed
4913 	Central Access Policy on the object was changed
4928 	An Active Directory replica source naming context was established
4929 	An Active Directory replica source naming context was removed
4930 	An Active Directory replica source naming context was modified
4931 	An Active Directory replica destination naming context was modified
4932 	Synchronization of a replica of an Active Directory naming context has begun
4933 	Synchronization of a replica of an Active Directory naming context has ended
4934 	Attributes of an Active Directory object were replicated
4935 	Replication failure begins
4936 	Replication failure ends
4937 	A lingering object was removed from a replica
4944 	The following policy was active when the Windows Firewall started
4945 	A rule was listed when the Windows Firewall started
4946 	A change has been made to Windows Firewall exception list. A rule was added
4947 	A change has been made to Windows Firewall exception list. A rule was modified
4948 	A change has been made to Windows Firewall exception list. A rule was deleted
4949 	Windows Firewall settings were restored to the default values
4950 	A Windows Firewall setting has changed
4951 	A rule has been ignored because its major version number was not recognized by Windows Firewall
4952 	Parts of a rule have been ignored because its minor version number was not recognized by Windows Firewall
4953 	A rule has been ignored by Windows Firewall because it could not parse the rule
4954 	Windows Firewall Group Policy settings has changed. The new settings have been applied
4956 	Windows Firewall has changed the active profile
4957 	Windows Firewall did not apply the following rule
4958 	Windows Firewall did not apply the following rule because the rule referred to items not configured on this computer
4960 	IPsec dropped an inbound packet that failed an integrity check
4961 	IPsec dropped an inbound packet that failed a replay check
4962 	IPsec dropped an inbound packet that failed a replay check
4963 	IPsec dropped an inbound clear text packet that should have been secured
4964 	Special groups have been assigned to a new logon
4965 	IPsec received a packet from a remote computer with an incorrect Security Parameter Index (SPI).
4976 	During Main Mode negotiation, IPsec received an invalid negotiation packet.
4977 	During Quick Mode negotiation, IPsec received an invalid negotiation packet.
4978 	During Extended Mode negotiation, IPsec received an invalid negotiation packet.
4979 	IPsec Main Mode and Extended Mode security associations were established.
4980 	IPsec Main Mode and Extended Mode security associations were established
4981 	IPsec Main Mode and Extended Mode security associations were established
4982 	IPsec Main Mode and Extended Mode security associations were established
4983 	An IPsec Extended Mode negotiation failed
4984 	An IPsec Extended Mode negotiation failed
4985 	The state of a transaction has changed
5024 	The Windows Firewall Service has started successfully
5025 	The Windows Firewall Service has been stopped
5027 	The Windows Firewall Service was unable to retrieve the security policy from the local storage
5028 	The Windows Firewall Service was unable to parse the new security policy.
5029 	The Windows Firewall Service failed to initialize the driver
5030 	The Windows Firewall Service failed to start
5031 	The Windows Firewall Service blocked an application from accepting incoming connections on the network.
5032 	Windows Firewall was unable to notify the user that it blocked an application from accepting incoming connections on the network
5033 	The Windows Firewall Driver has started successfully
5034 	The Windows Firewall Driver has been stopped
5035 	The Windows Firewall Driver failed to start
5037 	The Windows Firewall Driver detected critical runtime error. Terminating
5038 	Code integrity determined that the image hash of a file is not valid
5039 	A registry key was virtualized.
5040 	A change has been made to IPsec settings. An Authentication Set was added.
5041 	A change has been made to IPsec settings. An Authentication Set was modified
5042 	A change has been made to IPsec settings. An Authentication Set was deleted
5043 	A change has been made to IPsec settings. A Connection Security Rule was added
5044 	A change has been made to IPsec settings. A Connection Security Rule was modified
5045 	A change has been made to IPsec settings. A Connection Security Rule was deleted
5046 	A change has been made to IPsec settings. A Crypto Set was added
5047 	A change has been made to IPsec settings. A Crypto Set was modified
5048 	A change has been made to IPsec settings. A Crypto Set was deleted
5049 	An IPsec Security Association was deleted
5050 	An attempt to programmatically disable the Windows Firewall using a call to INetFwProfile.FirewallEnabled(FALSE
5051 	A file was virtualized
5056 	A cryptographic self test was performed
5057 	A cryptographic primitive operation failed
5058 	Key file operation
5059 	Key migration operation
5060 	Verification operation failed
5061 	Cryptographic operation
5062 	A kernel-mode cryptographic self test was performed
5063 	A cryptographic provider operation was attempted
5064 	A cryptographic context operation was attempted
5065 	A cryptographic context modification was attempted
5066 	A cryptographic function operation was attempted
5067 	A cryptographic function modification was attempted
5068 	A cryptographic function provider operation was attempted
5069 	A cryptographic function property operation was attempted
5070 	A cryptographic function property operation was attempted
5071 	Key access denied by Microsoft key distribution service
5120 	OCSP Responder Service Started
5121 	OCSP Responder Service Stopped
5122 	A Configuration entry changed in the OCSP Responder Service
5123 	A configuration entry changed in the OCSP Responder Service
5124 	A security setting was updated on OCSP Responder Service
5125 	A request was submitted to OCSP Responder Service
5126 	Signing Certificate was automatically updated by the OCSP Responder Service
5127 	The OCSP Revocation Provider successfully updated the revocation information
5136 	A directory service object was modified
5137 	A directory service object was created
5138 	A directory service object was undeleted
5139 	A directory service object was moved
5140 	A network share object was accessed
5141 	A directory service object was deleted
5142 	A network share object was added.
5143 	A network share object was modified
5144 	A network share object was deleted.
5145 	A network share object was checked to see whether client can be granted desired access
5146 	The Windows Filtering Platform has blocked a packet
5147 	A more restrictive Windows Filtering Platform filter has blocked a packet
5148 	The Windows Filtering Platform has detected a DoS attack and entered a defensive mode; packets associated with this attack will be discarded.
5149 	The DoS attack has subsided and normal processing is being resumed.
5150 	The Windows Filtering Platform has blocked a packet.
5151 	A more restrictive Windows Filtering Platform filter has blocked a packet.
5152 	The Windows Filtering Platform blocked a packet
5153 	A more restrictive Windows Filtering Platform filter has blocked a packet
5154 	The Windows Filtering Platform has permitted an application or service to listen on a port for incoming connections
5155 	The Windows Filtering Platform has blocked an application or service from listening on a port for incoming connections
5156 	The Windows Filtering Platform has allowed a connection
5157 	The Windows Filtering Platform has blocked a connection
5158 	The Windows Filtering Platform has permitted a bind to a local port
5159 	The Windows Filtering Platform has blocked a bind to a local port
5168 	Spn check for SMB/SMB2 fails.
5169 	A directory service object was modified
5170 	A directory service object was modified during a background cleanup task
5376 	Credential Manager credentials were backed up
5377 	Credential Manager credentials were restored from a backup
5378 	The requested credentials delegation was disallowed by policy
5379 	Credential Manager credentials were read
5380 	Vault Find Credential
5381 	Vault credentials were read
5382 	Vault credentials were read
5440 	The following callout was present when the Windows Filtering Platform Base Filtering Engine started
5441 	The following filter was present when the Windows Filtering Platform Base Filtering Engine started
5442 	The following provider was present when the Windows Filtering Platform Base Filtering Engine started
5443 	The following provider context was present when the Windows Filtering Platform Base Filtering Engine started
5444 	The following sub-layer was present when the Windows Filtering Platform Base Filtering Engine started
5446 	A Windows Filtering Platform callout has been changed
5447 	A Windows Filtering Platform filter has been changed
5448 	A Windows Filtering Platform provider has been changed
5449 	A Windows Filtering Platform provider context has been changed
5450 	A Windows Filtering Platform sub-layer has been changed
5451 	An IPsec Quick Mode security association was established
5452 	An IPsec Quick Mode security association ended
5453 	An IPsec negotiation with a remote computer failed because the IKE and AuthIP IPsec Keying Modules (IKEEXT) service is not started
5456 	PAStore Engine applied Active Directory storage IPsec policy on the computer
5457 	PAStore Engine failed to apply Active Directory storage IPsec policy on the computer
5458 	PAStore Engine applied locally cached copy of Active Directory storage IPsec policy on the computer
5459 	PAStore Engine failed to apply locally cached copy of Active Directory storage IPsec policy on the computer
5460 	PAStore Engine applied local registry storage IPsec policy on the computer
5461 	PAStore Engine failed to apply local registry storage IPsec policy on the computer
5462 	PAStore Engine failed to apply some rules of the active IPsec policy on the computer
5463 	PAStore Engine polled for changes to the active IPsec policy and detected no changes
5464 	PAStore Engine polled for changes to the active IPsec policy, detected changes, and applied them to IPsec Services
5465 	PAStore Engine received a control for forced reloading of IPsec policy and processed the control successfully
5466 	PAStore Engine polled for changes to the Active Directory IPsec policy, determined that Active Directory cannot be reached, and will use the cached copy of the Active Directory IPsec policy instead
5467 	PAStore Engine polled for changes to the Active Directory IPsec policy, determined that Active Directory can be reached, and found no changes to the policy
5468 	PAStore Engine polled for changes to the Active Directory IPsec policy, determined that Active Directory can be reached, found changes to the policy, and applied those changes
5471 	PAStore Engine loaded local storage IPsec policy on the computer
5472 	PAStore Engine failed to load local storage IPsec policy on the computer
5473 	PAStore Engine loaded directory storage IPsec policy on the computer
5474 	PAStore Engine failed to load directory storage IPsec policy on the computer
5477 	PAStore Engine failed to add quick mode filter
5478 	IPsec Services has started successfully
5479 	IPsec Services has been shut down successfully
5480 	IPsec Services failed to get the complete list of network interfaces on the computer
5483 	IPsec Services failed to initialize RPC server. IPsec Services could not be started
5484 	IPsec Services has experienced a critical failure and has been shut down
5485 	IPsec Services failed to process some IPsec filters on a plug-and-play event for network interfaces
5632 	A request was made to authenticate to a wireless network
5633 	A request was made to authenticate to a wired network
5712 	A Remote Procedure Call (RPC) was attempted
5888 	An object in the COM+ Catalog was modified
5889 	An object was deleted from the COM+ Catalog
5890 	An object was added to the COM+ Catalog
6144 	Security policy in the group policy objects has been applied successfully
6145 	One or more errors occured while processing security policy in the group policy objects
6272 	Network Policy Server granted access to a user
6273 	Network Policy Server denied access to a user
6274 	Network Policy Server discarded the request for a user
6275 	Network Policy Server discarded the accounting request for a user
6276 	Network Policy Server quarantined a user
6277 	Network Policy Server granted access to a user but put it on probation because the host did not meet the defined health policy
6278 	Network Policy Server granted full access to a user because the host met the defined health policy
6279 	Network Policy Server locked the user account due to repeated failed authentication attempts
6280 	Network Policy Server unlocked the user account
6281 	Code Integrity determined that the page hashes of an image file are not valid...
6400 	BranchCache: Received an incorrectly formatted response while discovering availability of content.
6401 	BranchCache: Received invalid data from a peer. Data discarded.
6402 	BranchCache: The message to the hosted cache offering it data is incorrectly formatted.
6403 	BranchCache: The hosted cache sent an incorrectly formatted response to the client's message to offer it data.
6404 	BranchCache: Hosted cache could not be authenticated using the provisioned SSL certificate.
6405 	BranchCache: %2 instance(s) of event id %1 occurred.
6406 	%1 registered to Windows Firewall to control filtering for the following:
6407 	%1
6408 	Registered product %1 failed and Windows Firewall is now controlling the filtering for %2.
6409 	BranchCache: A service connection point object could not be parsed
6410 	Code integrity determined that a file does not meet the security requirements to load into a process. This could be due to the use of shared sections or other issues
6416 	A new external device was recognized by the system.
6417 	The FIPS mode crypto selftests succeeded
6418 	The FIPS mode crypto selftests failed
6419 	A request was made to disable a device
6420 	A device was disabled
6421 	A request was made to enable a device
6422 	A device was enabled
6423 	The installation of this device is forbidden by system policy
6424 	The installation of this device was allowed, after having previously been forbidden by policy
7031  a service has stopped unexpectedly
8191 	Highest System-Defined Audit Message Value
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
DHCP
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#DHCP Server
PS51> Get-ChildItem C:\Windows\system32\dhcp\Dhcp*SrvLog-*.log | Select -ExpandProperty Name #Finding the Logs          
PS51> Get-DhcpServerAuditLog #make sure that the DHCP audit logs are enabled
#enable it and restart the DHCP service
PS51> Set-DhcpServerAuditLog -Enable $True -MaxMBFileSize 70
PS51> Restart-Service DhcpServer

DHCP settings-HKEY_LOCAL_MACHINE-SYSTEM-CurrentControlSet-Services-DHCPServer-Parameters.
? DhcpLogFilesMaxSize Sets the maximum file size for all logs. The default is 70 MB.
? DhcpLogDiskSpaceCleanupInterval Determines how often DHCP checks disk space usage and cleans up as necessary. The default interval is 60 minutes.
? DhcpLogMinSpaceOnDisk Sets the free space threshold for writing to the log. If the disk has less free space than the value specified, logging is temporarily disabled. The default value is 20 MB
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Event ID  Meaning
00	The log was started.
01	The log was stopped.
02	The log was temporarily paused due to low disk space.
10	A new IP address was leased to a client.
11	A lease was renewed by a client.
12	A lease was released by a client.
13	An IP address was found to be in use on the network.
14	A lease request could not be satisfied because the scope's address pool was exhausted.
15	A lease was denied.
16	A lease was deleted.
17	A lease was expired and DNS records for an expired leases have not been deleted.
18	A lease was expired and DNS records were deleted.
20	A BOOTP address was leased to a client.
21	A dynamic BOOTP address was leased to a client.
22	A BOOTP request could not be satisfied because the scope's address pool for BOOTP was exhausted.
23	A BOOTP IP address was deleted after checking to see it was not in use.
24	IP address cleanup operation has began.
25	IP address cleanup statistics.
30	DNS update request to the named DNS server.
31	DNS update failed.
32	DNS update successful.
33	Packet dropped due to NAP policy.
34	DNS update request failed.as the DNS update request queue limit exceeded.
35	DNS update request failed.
36	Packet dropped because the server is in failover standby role or the hash of the client ID does not match.
50+	Codes above 50 are used for Rogue Server Detection information
50: Unreachable domain
51: Authorization succeeded
52: Upgraded to a Windows Server 2003 operating system
53: Cached Authorization
54: Authorization failed
55: Authorization (servicing)
56: Authorization failure, stopped servicing
57: Server found in domain
58: Server could not find domain
59: Network failure
60: No DC is DS Enabled
61: Server found that belongs to DS domain
62: Another server found
63: Restarting rogue detection
64: No DHCP enabled interfaces
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#The Dynamic Host Configuration Protocol version 6 (DHCPv6) is a network protocol for configuring Internet Protocol version 6 (IPv6) hosts with IP addresses, IP prefixes and other configuration data required to operate in an IPv6 network. It is the IPv6 equivalent of the Dynamic Host Configuration Protocol for IPv4. 
Event ID  Meaning
11000	DHCPv6 Solicit.
11001	DHCPv6 Advertise.
11002	DHCPv6 Request.
11003	DHCPv6 Confirm.
11004	DHCPv6 Renew.
11005	DHCPv6 Rebind.
11006	DHCPv6 Decline.
11007	DHCPv6 Release.
11008	DHCPv6 Information Request.
11009	DHCPv6 Scope Full.
11010	DHCPv6 Started.
11011	DHCPv6 Stopped.
11012	DHCPv6 Audit log paused.
11013	DHCPv6 Log File.
11014	DHCPv6 Bad Address.
11015	DHCPv6 Address is already in use.
11016	DHCPv6 Client deleted.
11017	DHCPv6 DNS record not deleted.
11018	DHCPv6 Expired.
11019	DHCPv6 Leases Expired and Leases Deleted .
11020	DHCPv6 Database cleanup begin.
11021	DHCPv6 Database cleanup end.
11022	DNS IPv6 Update Request.
11023	DNS IPv6 Update Failed.
11024	DNS IPv6 Update Successful.
11028	DNS IPv6 update request failed as the DNS update request queue limit exceeded.
11029	DNS IPv6 update request failed.
11030	DHCPv6 stateless client records purged.
11031	DHCPv6 stateless client record is purged as the purge interval has expired for this client record.
11032	DHCPV6 Information Request from IPV6 Stateless Client.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------