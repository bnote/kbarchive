---
layout: page
title: "Q166283: Cannot Install RIP for Internet Protocol"
permalink: /kb/166/Q166283/
---

## Q166283: Cannot Install RIP for Internet Protocol

{% raw %}

	Article: Q166283
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When the Routing tab in TCP/IP properties is open, you may receive the following
	message:
	
	  IP forwarding (IP Routing) allows packets to be forwarded on a multi-
	  homed system. The routing information may be static, or may be
	  collected by RIP for Internet Protocol. RIP is a service that can be
	  installed from the Network Control Panel service page.
	
	However, when you check the Services tab in Network properties, you do not see
	RIP for Internet Protocol.
	
	CAUSE
	=====
	
	RIP for Internet Protocol is not available in Windows NT Workstation unless you
	install SP4. It is available in Windows NT Server only.
	
	RESOLUTION
	==========
	
	Upgrade to Windows NT Server, use a static route table, or obtain and install
	SP4. For information about how to do so, see the following article in the
	Microsoft Knowledge Base:
	
	  ARTICLE- ID: Q172514
	  TITLE : Silent RIP for IP Available for Windows NT Workstation
	
	MORE INFORMATION
	================
	
	This is a documentation error. The RIP for Internet Protocol service that is
	referred to on the Routing tab is used to allow dynamic routing with TCP/IP.
	This service is a component of Windows NT Server 4.0, and is not included with
	Windows NT Workstation 4.0.
	
	You cannot use dynamic routing with Windows NT Workstation. However, static IP
	routing can be enabled in Windows NT Workstation. The routing tables must be
	manually established by using the ROUTE command to create the static routing
	table on a multihomed computer.
	
	To view the message, perform the following steps:
	
	1. In Control Panel, double-click Network.
	
	2. Click the Protocols tab.
	
	3. Double-click the TCP/IP protocol.
	
	4. Click the Routing tab.
	
	REFERENCES
	==========
	
	For additional information, see the following article in the Microsoft Knowledge
	Base:
	
	  ARTICLE-ID: Q140859
	  TITLE : TCP/IP Routing Basics for Windows NT
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search
	Version           : 4.0
	
	=============================================================================
	

{% endraw %}
