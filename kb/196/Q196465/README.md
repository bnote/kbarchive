---
layout: page
title: "Q196465: Err Msg: Your Password Must Be at Least 0 Characters Long..."
permalink: /kb/196/Q196465/
---

## Q196465: Err Msg: Your Password Must Be at Least 0 Characters Long...

{% raw %}

	Article: Q196465
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it
	if a problem occurs. For information on how to do this, view the
	"Restoring the Registry" online Help topic in Regedit.exe or the
	"Restoring a Registry Key" online Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	When a user attempts to change his or her password from a computer running
	Windows NT, he or she is presented with the following error message:
	
	  Your password must be at least 0 characters long. Your new password
	  cannot be the same as any of your previous 0 passwords. Also, your site
	  may require passwords that must be a combination of upper case, lower
	  case, numbers, and non-alphanumeric characters. Type a password which
	  meets these requirements in both text boxes.
	
	CAUSE
	=====
	
	This problem occurs when the registry entry for strong passwords (PASSFILT)
	exists, but your current account policy has no password restrictions.
	
	RESOLUTION
	==========
	
	Passfilt.dll implements the following password policy:
	
	1. Passwords must be at least six (6) characters long.
	
	2. Passwords must contain characters from at least three (3) of the following
	  four (4) classes:
	
	     Description                             Examples
	     -------------------------------------------------------------------
	
	     English upper case letters              A, B, C, ... Z
	     English lower case letters              a, b, c, ... z
	     Westernized Arabic numerals             0, 1, 2, ... 9
	     Non-alphanumeric                        ("special characters") such
	                                             as punctuation symbols
	
	3. Passwords may not contain your user name or any part of your full name.
	
	If your current account policy is set to permit blank password, this conflicts
	with the above requirements for PASSFILT. Therefore, you should change the
	Minimum Password Length value to be at least six characters, or disable the
	functionality of PASSFILT. To disable PASSFILT, complete the following steps on
	the PDC:
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it. If
	you are running Windows NT, you should also update your Emergency Repair Disk
	(ERD).
	
	1. Use Registry Editor (Regedt32.exe) to navigate to the following key:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa
	
	2. Double-click the "Notification Packages" key and remove the following value:
	
	  PASSFILT
	
	3. Click OK and then exit Registry Editor.
	
	4. Shut down and restart the computer running Windows NT Server.
	
	MORE INFORMATION
	================
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q161990 How to Enable Strong Password Functionality in Windows NT
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : WinNT:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
