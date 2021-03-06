---
layout: page
title: "Q190949: SMS: PREINST /SYNCPARENT Leaves Blank Records in Machine Groups"
permalink: /kb/190/Q190949/
---

## Q190949: SMS: PREINST /SYNCPARENT Leaves Blank Records in Machine Groups

{% raw %}

	Article: Q190949
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 18-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you perform a PREINST /SYNCPARENT to update inventory at a parent site,
	records that are deleted from the child site may result in blank records in your
	Systems Management Server machine groups on the parent site.
	
	CAUSE
	=====
	
	When the PREINST /SYNCPARENT process runs, the child site sends all of its
	inventory to the parent. When the parent processes this inventory, it will
	remove any records from its database that have been deleted on the child site.
	When the parent site deletes these records, it does not check to see if the
	deleted computers are members of any Systems Management Server machine groups.
	The machine groups will be left with blank records that point to the computers
	that were deleted.
	
	WORKAROUND
	==========
	
	To work around this problem, try any one of the following:
	
	- Manually delete each record from the Parent sites when they are deleted from
	  the child site.
	
	-or-
	
	- After going through the PREINST /SYNCPARENT process, look at each machine
	  group on the parent site and delete any blank records.
	
	-or-
	
	- Use the DELMIF trigger to automatically delete all computers from the parent
	  when a computer is deleted from the child site. For more information on the
	  DELMIF trigger, see the following article in the Microsoft Knowledge Base;
	
	  Q188051 SMS: Delmif.exe Syntax, Description, and Usage
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 1.2. We are researching this problem and will post additional
	information here in the Microsoft Knowledge Base as it becomes available.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          :  
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
