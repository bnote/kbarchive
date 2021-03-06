---
layout: page
title: "Q255262: Changes to Site Control File Are Lost After the File Is 434KB"
permalink: /kb/255/Q255262/
---

## Q255262: Changes to Site Control File Are Lost After the File Is 434KB

{% raw %}

	Article: Q255262
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): kbsms200 kbsms200bug kbsms120 kbsms120bug
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When you try to add addresses for new secondary sites, the Site Control file may
	not be updated with the new site information. Also, the Proposed Change window
	may not become populated when you make changes.
	
	CAUSE
	=====
	
	This problem can occur when the Sitectrl.ct0 file has reached a defined limit.
	The current limit is 454,000 bytes, or approximately 434 kilobytes (KB) on disk.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To resolve this problem, replace the Base4.dll file on the Site Server with the
	file referenced below, add a required registry value, and then restart the
	server:
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English-language version of this software update should have the following
	file attributes or later:
	
	  Date        Time      Size     File name     Platform   Version
	  -----------------------------------------------------------------------
	  03/28/2000  09:23pm   538,656  Base4.dll     I386       1.2.0.0
	
	
	
	In addition to replacing the preceding file, the following registry value must be
	added before restarting the server. This value is read in at run time, and now
	defines the size of the Site Control file. If no value exists, the default value
	of 454,000 bytes is the maximum size of the Site Control file.
	
	1. Use Registry Editor (Regedt32.exe) to view the following registry key:
	
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\Components\SMS_SITE_CONFIG_MANAGER
	
	2. On the Edit menu, click Add Value, and then add the following registry value:
	
	  Value Name: SiteControlImageSize
	  Data Type:  REG_DWORD
	  Value:      454000 - 681000 (in decimal)
	
	3. Quit Registry Editor.
	
	NOTE: When you enter the value, confirm that you enter it as decimal. Otherwise,
	567500 as hexadecimal is equal to approximately 5 megabytes (MB). The range in
	hexadecimal is from 0x0006ED70 to 0x000A6428. If you are experiencing this
	problem, a good starting value would be 567500, or 0x0008A8CC in hexadecimal.
	
	To work around this problem, create another Central Site and attach Primary Sites
	to this Central Site to reduce the size of the Site Control File.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 1.2.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200 kbsms200bug kbsms120 kbsms120bug 
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
