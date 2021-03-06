---
layout: page
title: "Q232653: SMSCliToknAcct&amp; Locked Out When Hardware Inventory Is Enabled"
permalink: /kb/232/Q232653/
---

## Q232653: SMSCliToknAcct&amp; Locked Out When Hardware Inventory Is Enabled

{% raw %}

	Article: Q232653
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0
	Operating System(s): 
	Keyword(s): kbnetwork kbClient kbSecurity kbServer kbsms200 kbsms200bug kbInventory kbSoftwareDist
	Last Modified: 25-JUN-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you add clients to a Systems Management Server site and enable the
	hardware inventory client component, administrators may observe the following
	symptoms involving account lockouts and/or software distribution failure:
	
	- Software distribution fails to connect because the SMSCliToknAcct&
	  account is locked out.
	
	- The SMSCliToknAcct& is continually locked out in the domain accounts
	  database or in individual local accounts databases of Systems Management
	  Server Clients.
	
	This issue only occurs on sites which have enabled the hardware inventory agent.
	
	CAUSE
	=====
	
	When enumerating the Win32_LogicalDisk class for hardware inventory the
	SMSCliToknAcct& local account is used to access network drives. The remote
	system has the SMSCliToknAcct& if it is a client, but may have a different
	password. This causes a password failure and eventually locks the account.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Systems Management
	Server version 2.0. For additional information, please see the following article
	in the Microsoft Knowledge Base:
	
	  Q236325 How to Obtain the Latest Systems Management Server 2.0 Service Pack
	
	
	
	WORKAROUND
	==========
	
	There are also two possible workarounds for this issue:
	
	- Disable account lockouts on the domain and on individual site systems that
	  are not domain controllers to prevent the lockouts from occurring.
	
	- Disable enumeration of the Win32_LogicalDisk class in the SMS_DEF.MOF file
	  for the site. For more information on how to do this see chapter 10 of the
	  Microsoft Systems Management Server Administrator's Guide.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 2.0. This problem was first corrected in Systems Management Server
	version 2.0 Service Pack 2.
	
	MORE INFORMATION
	================
	
	To install the pre-SP1 version of this hotfix, perform the following steps on
	the Systems Management Server site server:
	
	1. Stop the SMS_SITE_COMPONENT_MANAGER and SMS_EXECUTIVE services.
	
	2. Copy the updated Inhinv32.exe file to the following folder:
	
	  \SMS\Inboxes\Clicomp.src\Hinv\<Platform>
	
	3. Copy the updated Wbemsdk.exe file to the following folder:
	
	  \SMS\Inboxes\Clicomp.src\Wbem\<Platform>
	
	4. Copy the updated Sms_def.mof file to the following folder:
	
	  \SMS\Inboxes\Clifiles.src\Hinv
	
	5. Copy the updated Compver.ini file to the following locations:
	
	   - \SMS\Inboxes\Clicomp.src\Hinv
	   - \SMS\Inboxes\Clicomp.src\Wbem
	
	6. Copy the updated Hinv32.exe file to the following folder:
	
	  \SMS\Bin\<Platform>
	
	  NOTE: The Hinv32.exe file is not included as a separate file, it is embedded
	  in the Inhinv32.exe file. To extract it, run "inhinv32.exe /x" (without the
	  quotation marks) and select the file to extract.
	
	7. Start the SMS_SITE_COMPONENT_MANAGER and SMS_EXECUTIVE services.
	
	NOTE: Once the SMS Inbox Manager component updates the Client Access Points
	(CAP), the client will be able to access the updated files. The default Client
	Configuration Installation Manager (CCIM) polling interval is 23 hours.
	Therefore, it may take up to 23 hours for the hotfixed files to be propagated to
	the clients. To speed up this process, you can stop and restart the SMS Client
	Service on each client. You can also create a software distribution for one of
	the Resource Kit tools Setevnt.exe or Cliutils.exe along with the appropriate
	parameter(s) to start a CCIM work cycle. For information on the proper syntax to
	use with these tools, see the Resource Kit documentation.
	
	To install the Post-SP1 hotfix, perform the following steps on the Systems
	Management Server site server:
	
	1. Stop the SMS_SITE_COMPONENT_MANAGER and SMS_EXECUTIVE services.
	
	2. Copy the updated Compver.ini file to the following folder:
	
	  \SMS\Inboxes\Clicomp.src\Hinv
	
	3. Copy the updated Inhinv32.exe file to the following folder:
	
	  \SMS\Inboxes\Clicomp.src\Hinv\<Platform>
	
	4. Copy the updated Sms_def.mof file to the following folder:
	
	  \SMS\Inboxes\Clifiles.src\Hinv
	
	  NOTE: If the existing Sms_def.mof file has been modified to change the
	  information gathered by the 32-bit hardware inventory agent, those changes
	  have to be made to the replacement Sms_def.mof file to obtain the same
	  inventory information after you apply this fix.
	
	5. Copy the updated Hinv32.exe file to the following folder:
	
	  \SMS\Bin\<Platform>
	
	  NOTE: The Hinv32.exe file is not included as a separate file, it is embedded
	  in the Inhinv32.exe file. To extract it, run "inhinv32.exe /x" (without the
	  quotation marks) and select the file to extract.
	
	6. Start the SMS_SITE_COMPONENT_MANAGER and SMS_EXECUTIVE services.
	
	NOTE: The default Client Configuration Installation Manager (CCIM) polling
	interval is 23 hours. Therefore, it may take up to 23 hours for the hotfixed
	files to be propagated to the clients. To speed up this process, you can stop
	and restart the SMS Client Service on each client. You can also create a
	software distribution for one of the Resource Kit tools Setevnt.exe or
	Cliutils.exe along with the appropriate parameter(s) to start a CCIM work cycle.
	For information on the proper syntax to use with these tools, see the Resource
	Kit documentation.
	
	All Systems Management Server clients have the SMSCliToknAcct& account in the
	local accounts database while all Domain Controllers share a single
	SMSCliToknAcct& from the domain accounts database.
	
	The SMSCliToknAcct& account is used to launch installations in several
	specific situations:
	
	- The "Run with administrative rights" option is enabled for a program that
	  isn't also configured to use the Windows NT client software installation
	  account.
	
	- The program is set to run "Whether or not a user is logged on" and the
	  program isn't configured to use the Windows NT client software installation
	  account.
	
	- The program is set to run "Only when no user is logged on" and isn't
	  configured to use the Windows NT client software installation account.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbnetwork kbClient kbSecurity kbServer kbsms200 kbsms200bug kbInventory kbSoftwareDist kbsms200sp1fix kbsms200sp2fix kbfixlist
	Technology        : kbSMSSearch kbSMS200
	Version           : winnt:2.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
