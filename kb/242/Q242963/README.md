---
layout: page
title: "Q242963: SMS: Slow Enumeration of Existing Collections"
permalink: /kb/242/Q242963/
---

## Q242963: SMS: Slow Enumeration of Existing Collections

{% raw %}

	Article: Q242963
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0,2.0 SP1
	Operating System(s): 
	Keyword(s): kbsms200bug kbsms200fix kbsms200sp2fix
	Last Modified: 25-JUN-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You may experience slow enumeration of collections when you are using the
	Systems Management Server (SMS) Administrator console to view or refresh
	collections under:
	
	  Systems Management Server
	       Site Database (<site code> - <site name>)
	          Collection
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Systems Management
	Server version 2.0. For additional information, please see the following article
	in the Microsoft Knowledge Base:
	
	  Q236325 How to Obtain the Latest Systems Management Server 2.0 Service Pack
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 2.0. This problem was first corrected in Systems Management Server
	version 2.0 Service Pack 2.
	
	MORE INFORMATION
	================
	
	This hotfix must be installed on the computer that contains the SMS provider,
	which can be either the SMS site server or the computer serving as the SQL
	server.
	
	To install the hotfix on i386-based computers:
	
	1. Log on to your site server (or the computer containing the SMS provider)
	  using an account with administrative privileges.
	
	2. Close all SMS Administrator consoles.
	
	3. Use the Services tool in Control Panel to stop Site Component Manager and
	  then Windows Management.
	
	4. Run the Q242963.exe hotfix file you received. Follow the instructions in the
	  wizard.
	
	5. Use the Services tool in Control Panel to start Site Component Manager and
	  then Windows Management.
	
	To install the hotfix on Alpha-based computers
	
	1. Log on to your site server (or the computer containing the SMS provider)
	  using an account with administrative privileges.
	
	2. Close all SMS Administrator consoles.
	
	3. Use the Services tool in Control Panel to stop Site Component Manager and
	  then Windows Management.
	
	4. Copy the Smsprov.dll file to SMS\BIN\Alpha\Smsprov.dll.
	
	5. Copy the Sms_ncol.dll file to SMS\BIN\Alpha\Sms_ncol.dll.
	
	6. Use the Services tool in Control Panel to start Site Component Manager and
	  then Windows Management.
	
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200bug kbsms200fix kbsms200sp2fix 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1
	Version           : winnt:2.0,2.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
