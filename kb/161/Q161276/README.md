---
layout: page
title: "Q161276: Error Message Installing GSNW in a NetWare 4.x Environment"
permalink: /kb/161/Q161276/
---

## Q161276: Error Message Installing GSNW in a NetWare 4.x Environment

{% raw %}

	Article: Q161276
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbenv kbnetwork kbui
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you install Gateway Services for NetWare (GSNW), the following error
	message may appear when you attempt to add a share in the Configure Gateway
	dialog box on the Windows NT Server computer:
	
	  The specified user does not exist. To create a gateway share, both the
	  currently logged on user and the gateway account must have access to the
	  NetWare resource. Also, the gateway account must be in the NTGateway group on
	  the NetWare server and the current user must have the right to create a share
	  on the local computer.
	
	This will happen even if the above statement is true.
	
	CAUSE
	=====
	
	The most likely cause for this problem is the Gateway Account is set
	incorrectly.
	
	If bindery emulation is not enabled on the Novell NetWare 4.x server and the
	gateway is enabled in Windows NT, the fully qualified NDS user name must be
	specified by the GSNW tool in Control Panel. To do this, double- click the GSNW
	icon in Control Panel, click Gateway, click Enable Gateway so that it is
	selected, and then enter the Gateway Account information.
	
	NOTE: The NTGATEWAY group and NTUSER accounts do not have to be in the same
	context of the NetWare server as long as they have access to the server volume.
	
	The following is an example of how the Gateway Account should be set:
	
	  ntuser.users.lcipx (or cn=ntuser.ou=users.o=lcipx)
	
	If only NTUSER is specified here, then it assumes the connection to the NetWare
	server should be using bindery emulation and the same error happens.
	
	In this case, bindery emulation should be enabled at the NetWare server (SET
	BINDERY CONTEXT=users.lcipx, in this example, at the console, or in
	Autoexec.ncf). Both NTUSER and NTGATEWAY accounts SHOULD be under the same
	context also. Otherwise, the system will display the following error:
	
	  To create a gateway share, both the currently logged on user and the gateway
	  account must have access to the NetWare resource. Also, the gateway account
	  must be in the NTGateway group on the NetWare server and the current user
	  must have the right to create a share on the local computer.
	
	This error can occur if a fully qualified name for the Gateway account is not
	specified. By enabling bindery emulation, the fully qualified name is no longer
	an issue, and therefore fixes the problem.
	
	WORKAROUND
	==========
	
	Create and use a different account in the NTGateway group on the NetWare Server
	computer. Make sure that the same account and password created on the Windows NT
	Server computer is a member of the administrators group and is used to log on to
	the Windows NT Server computer when you install GSNW.
	
	-or-
	
	Enable bindery emulation on the NetWare server computer.
	
	MORE INFORMATION
	================
	
	For more information, please see the following Microsoft Knowledge Base
	articles:
	
	  ARTICLE-ID: Q142639
	  TITLE : Windows NT 4.0 Readme.wri File (Part 1 of 5) Section: Creating a
	  Gateway to an NDS Volume
	
	  ARTICLE-ID: Q118469
	  TITLE : GSNW Gateway Requires NTGATEWAY Group
	
	Additional query words: gsnw nt netware
	
	======================================================================
	Keywords          : kbenv kbnetwork kbui 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
