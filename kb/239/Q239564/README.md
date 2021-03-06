---
layout: page
title: "Q239564: SMS: Client Components Reinstalled During Periodic Verification"
permalink: /kb/239/Q239564/
---

## Q239564: SMS: Client Components Reinstalled During Periodic Verification

{% raw %}

	Article: Q239564
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0,2.0 SP1
	Operating System(s): 
	Keyword(s): kbClient kbsms200 kbsms200bug kbsms200sp2fix
	Last Modified: 25-JUN-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Systems Management Server (SMS) 2.0 client components may be reinstalled during
	the Client Configuration Installation Manager (CCIM) periodic (30-day)
	verification. Because all base and optional components are reinstalled,
	components such as hardware and software inventory are taken regardless of your
	schedule.
	
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
	
	To install the hotfix:
	
	1. Log on to your site server using an account with administrative privileges.
	
	2. On the site server, close the SMS Administrator console.
	
	3. Run Q239564.exe and follow the directions in the wizard.
	
	This hotfix is one part of a set of two hotfixes. You should install both
	hotfixes for best results. For additional information about the second hotfix,
	click the article number below to view the article in the Microsoft Knowledge
	Base:
	
	  Q238144 SMS: Client Installation Corrupts Path Statement in Autoexec.bat
	
	
	After Q239564.exe is installed, allow the updated Compver.ini and Clicore.exe
	files to be propagated to all Logon Points and Client Access Points (CAPS) in
	the site.
	
	NOTE: The default Client Configuration Installation Manager (CCIM) polling
	interval is 23 hours. Therefore, it may take up to 23 hours for the hotfixed
	files to be propagated to the clients. To speed up this process, use any of the
	following methods:
	
	- Stop and restart the SMS Client Service on each client. For Microsoft Windows
	  NT, simply stop and restart the service. For Microsoft Windows 95 or
	  Microsoft Windows 98, a restart is required.
	
	- Create a software distribution for one of the Resource Kit tools (Setevnt.exe
	  or Cliutils.exe), along with the appropriate parameters to start a CCIM work
	  cycle. The tools are located on SMS 2.0 CD-ROM 2.
	
	  For Setevnt.exe the syntax is:
	
	  setevnt /q
	
	For Cliutils.exe, the syntax is:
	
	  Cliutils KICK "Client Configuration Installation Manager"
	
	- If you have the Networking Logon Client Installation option enabled, have
	  users log off and back on.
	
	- Have users run SMSMan manually.
	
	NOTE: Windows 95/98 clients may require a restart after the hotfixed files have
	been installed to receive full hotfix functionality. To verify this, review the
	Clicore.log file after the update. If a restart is required, the entry listed
	below will be logged. Because of the nature of this hotfix, Microsoft recommends
	that a mandatory restart policy be used for all Windows 95/98 users after the
	hotfix has been applied.
	
	  Reboot required - disabling component until reboot
	
	Additional query words: prodsms 30 day verify reinstall
	
	======================================================================
	Keywords          : kbClient kbsms200 kbsms200bug kbsms200sp2fix 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1
	Version           : winnt:2.0,2.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
