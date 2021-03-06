---
layout: page
title: "Q214892: Cannot Install SMS Client on a Workgroup Member"
permalink: /kb/214/Q214892/
---

## Q214892: Cannot Install SMS Client on a Workgroup Member

{% raw %}

	Article: Q214892
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbnetwork
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to install the Systems Management Server (SMS) client software
	on a computer that is a workgroup member and is running Microsoft Windows NT
	Workstation, you may receive the following error message in the Clicfg.log
	file:
	
	  Network path not found
	
	CAUSE
	=====
	
	This behavior can occur when the computer unsuccessfully attempts to use NetBIOS
	name resolution to locate an SMS server on the network.
	
	RESOLUTION
	==========
	
	To prevent this problem from occurring, use either of the following methods:
	
	- If your computer uses the Microsoft Windows Internet Naming Service (WINS)
	  for NetBIOS name resolution, verify that your computer can communicate with
	  the WINS server. For information about troubleshooting WINS issues, please
	  see the following article in the Microsoft Knowledge Base:
	
	  Q169790How to Troubleshoot Basic TCP/IP Problems in Windows NT 4.0
	
	- If your computer does not use WINS, you can use an LMHOSTS file on your
	  computer to identify the NetBIOS name and TCP/IP address of the SMS server.
	  For information about creating an LMHOSTS file, please see the following
	  article in the Microsoft Knowledge Base:
	
	  Q180094How to Write an LMHOSTS File for Domain Validation
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kberrmsg kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTW400sp4 kbWinNTW400sp3 kbWinNTW400sp2 kbWinNTW400sp1
	Version           : winnt:4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4
	Hardware          : ALPHA x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
