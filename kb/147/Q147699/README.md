---
layout: page
title: "Q147699: Logging On To Windows NT Domain Bypassing The Logon Screens"
permalink: /kb/147/Q147699/
---

## Q147699: Logging On To Windows NT Domain Bypassing The Logon Screens

{% raw %}

	Article: Q147699
	Product(s): Windows for Workgroups and Windows NT Networking Issues
	Version(s): WINDOWS:; winnt:3.5,3.51
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51 
	- Microsoft Windows NT Server versions 3.5, 3.51 
	- Microsoft Windows for Workgroups 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article explains how to log on to a Windows NT domain in Windows for
	Workgroups by bypassing the logon screens. Consult with your network or systems
	administrator to make sure this procedure does not violate your network
	environment policies.
	
	
	MORE INFORMATION
	================
	
	When you start Windows for Workgroups, a dialog box appears that requests your
	username and password. If you are a member of a domain, another dialog box
	appears that requests your domain name, domain user name and domain password.
	This article describes the following procedures:
	
	- Bypassing Domain Logon
	
	- Bypassing Windows for Workgroups and Domain Logons
	
	Bypassing Domain Logon
	----------------------
	
	To bypass the Domain logon screen:
	
	1. Create or verify your user account and password in User Manager for Domains
	  on the Windows NT Server.
	
	2. If you have a user name and password for the Windows for Workgroups logon,
	  use File Manager to search for a *.PWL file in the WINDOWS directory. The
	  file name is usually the first eight characters of your user name with the
	  PWL extension. For example, if your user name is Myname, then the file name
	  is MYNAME.PWL. Delete the file.
	
	3. In Control Panel Network, enter the default logon name and click Startup.
	  Select the "Log On at Startup" and the "Log Onto Windows NT Domain" check
	  boxes. Quit Control Panel Network and restart Windows for Workgroups.
	
	4. An
	
	  Error 2: The specified file was not found
	
	  error message appears. This is expected because the *.PWL file does not exist.
	  Click OK.
	
	5. Enter a your user name and password in the Windows for Workgroups logon
	  screen. Click OK. Click Yes to create the password list file (*.PWL). Then,
	  confirm your password.
	
	6. Enter your Windows NT domain user name and password in the Domain logon
	  screen. Select the "Save this Password" check box and click OK.
	
	7. If the Windows NT domain user name and password is valid, a message apears
	  that indicates a successful logon to the domain. If you do not want this
	  message to appear, click Startup in Control Panel Network. Clear the "Don't
	  Display Message on Successful Logon" check box.
	
	8. Log off and log back on using the Logon On/Off utility or the Log On/Off
	  option in Control Panel Network. Only the Windows for Workgroups logon screen
	  appears, bypassing the Windows NT domain logon screen.
	
	Bypassing Windows for Workgroups and Domain Logons
	--------------------------------------------------
	
	To bypass both the Windows for Workgroups and the Domain logon screens:
	
	1. Create or verify your user account and blank password in User Manager for
	  Domains on the Windows NT Server.
	
	2. If you have a user name and password for the Windows for Workgroups logon,
	  use File Manager to search for a *.PWL file in the WINDOWS directory. The
	  file name is usually the first eight characters of your user name with the
	  PWL extension. For example, if your user name is Myname, then the file name
	  is MYNAME.PWL. Delete the file.
	
	3. In Control Panel Network, enter the default logon name and click Startup.
	  Select the "Log On at Startup" and the "Log Onto Windows NT Domain" check
	  boxes. Quit Control Panel Network and restart Windows for Workgroups.
	
	4. An
	
	  Error 2: The specified file was not found
	
	  error message appears. This is expected because the *.PWL file does not exist.
	  Click OK.
	
	5. Enter the user name only in the Windows for Workgroups logon screen. Do not
	  enter a password. Click OK. Click Yes to create the password list file
	  (*.PWL). Do not enter a password for password confirmation. Click OK.
	
	6. Enter your Windows NT domain user name only in the Domain logon screen. Do
	  not enter a password. Select the "Save this Password" check box.
	
	7. If the Windows NT domain user name and password is valid, a message apears
	  that indicates a successful logon to the domain. If you do not want this
	  message to appear, click Startup in Control Panel Network. Clear the "Don't
	  Display Message on Successful Logon" check box.
	
	8. Log off and log back on using the Logon On/Off utility or the Log On/Off
	  option in Control Panel Network. Only the Windows for Workgroups logon screen
	  appears, bypassing the Windows NT domain logon screen.
	
	Additional query words: 3.11 wfw wfwg
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search kbAudDeveloper kbWFWSearch
	Version           : WINDOWS:; winnt:3.5,3.51
	
	=============================================================================
	

{% endraw %}
