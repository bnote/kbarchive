---
layout: page
title: "Q121388: Controlling LM and NT Logon Script Configurations with SMS"
permalink: /kb/121/Q121388/
---

## Q121388: Controlling LM and NT Logon Script Configurations with SMS

{% raw %}

	Article: Q121388
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.0,1.1,1.2
	Operating System(s): 
	Keyword(s): kbnetwork kbSCMan kbsmsAdmin smsadmin smssiteconfigman
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 1.0, 1.1, 1.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This information applies to Microsoft LAN Manager and Windows NT products only.
	For information on NetWare script modifications, refer to other articles in the
	Microsoft Knowledge Base.
	
	Selecting the Automatically Configure Logon Scripts option in Systems Management
	Server Administrator causes Systems Management Server to attempt modifications
	to both user account profiles and existing logon scripts for those users. To
	prevent these modifications from happening to selected accounts, the
	administrator can alter the behavior of Systems Management Server to accommodate
	the needs of network users.
	
	MORE INFORMATION
	================
	
	1. The Systems Management Server Site Configuration Manager will only attempt to
	  modify a users profile if it is blank (no logon script specified), or if it
	  already contains the SMSLS script name.
	
	  If an existing script is detected that is not SMSLS, Systems Management Server
	  then performs several operations:
	
	  a. Systems Management Server first makes a copy of the script as it exists in
	     the REPL$\SCRIPTS directory using a temporary name. The temporary file
	     will be opened and the following two (start and end) encapsulation comment
	     strings will be looked for:
	
	      - Systems Management Server 1.0:
	
	              REM Microsoft Systems Management Server (start)
	
	              REM SMS Build <xxx>
	              if "%OS%" == "Windows_NT" call smsls
	              if "%OS%" == "" call %0\..\smsls
	
	              REM Microsoft Systems Management Server (end)
	
	      - Systems Management Server 1.1:
	
	              REM Microsoft Systems Management Server (start)
	
	              REM SMS Build 692
	
	              call %0\..\smsls
	
	              REM Microsoft Systems Management Server (end)
	
	  b. If the start and end strings are present, the file will not be modified
	     (allowing the administrator to edit the changes between them and preserve
	     them). If these strings are not present they will be added in, either at
	     the top of the script or appended to the bottom of the script depending on
	     the selections made in Systems Management Server Administrator (<Site
	     Properties><Clients>). The modified file will then replace the
	     actual script file and the original script file will be saved with a
	     sequentially numbered extension like "000".
	
	2. If the script specified does not include either a .BAT or .CMD file
	  extension, Systems Management Server will ignore this script and will not
	  attempt items 1a or 1b above. This is by design for Systems Management Server
	  version 1.0 to provide the administrator with the capability of bypassing
	  certain user accounts from the Systems Management Server logon script
	  automatic configuration. This feature is under review and will be considered
	  for inclusion in a future release.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnetwork kbSCMan kbsmsAdmin smsadmin smssiteconfigman 
	Technology        : kbSMSSearch kbSMS100 kbSMS110 kbSMS120
	Version           : winnt:1.0,1.1,1.2
	
	=============================================================================
	

{% endraw %}
