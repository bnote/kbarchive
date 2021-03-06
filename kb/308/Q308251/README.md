---
layout: page
title: "Q308251: FIX: Forms, Menus, Reports Corrupted on Windows 2000 After Cycle"
permalink: /kb/308/Q308251/
---

## Q308251: FIX: Forms, Menus, Reports Corrupted on Windows 2000 After Cycle

{% raw %}

	Article: Q308251
	Product(s): Microsoft FoxPro
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbvfp600bug kbGrpDSFox kbDSupport kbvfp700fix
	Last Modified: 17-JAN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0, used with:
	   - the operating system: Microsoft Windows 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A form, menu, or report is created or modified in Visual FoxPro 6.0 on a
	computer running Windows 2000. After the computer is improperly shut down and
	restarted, subsequent attempts to modify the file may fail.
	
	This problem seems to occur no matter what method is used to create or modify the
	file, and regardless of the state of Visual FoxPro (open or closed) when the
	computer loses power. In fact, this problem has the potential to corrupt files
	that were opened since the last clean shutdown of Windows 2000.
	
	NOTE: This problem occurs with Visual FoxPro 6.0 Service Pack 3 (SP3), SP4, and
	SP5. It does not occur with the original version of Visual FoxPro 6.0 (build
	8167).
	
	CAUSE
	=====
	
	An optimization was introduced in Visual FoxPro 6.0 SP3 which was intended to
	increase the speed of saving forms, menus, and reports. Unfortunately, this
	optimization involves flagging these files in a way that causes them to not be
	committed to disk unless a clean shutdown of Windows 2000 occurs.
	
	WORKAROUND
	----------
	
	To avoid this problem, you can disable the Write Cache Enabled setting on the
	local hard drive(s) on the Windows 2000 computer. Note however that Windows 2000
	Service Pack 1 (SP1) or later is needed for this setting to persist. The RTM
	version of Windows 2000 does not persist this setting between restarts.
	
	To adjust this setting, follow these steps:
	
	1. Open My Computer, right-click the local hard drive, and click Properties.
	
	2. Click the Hardware tab, select the local hard drive in the list of drives,
	  and then click Properties.
	
	3. Click the Disk Properties tab and clear the Write Cache Enabled checkbox.
	
	4. Perform steps 1 through 3 for each hard drive on the local computer, and then
	  restart the computer.
	
	NOTE: Because this workaround has the potential to degrade performance on large
	IDE drives, it is recommended that you upgrade to Visual FoxPro 7.0 to resolve
	this issue.
	
	STATUS
	======
	
	This problem was corrected in Microsoft Visual FoxPro version 7.0 for Windows.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start Visual FoxPro 6.0 SP3 or later on a computer running Windows 2000.
	
	2. Create or modify a form (by selecting New from the File menu, using the
	  CREATE FORM command, and so on).
	
	3. Add several controls to the form and then save it.
	
	4. Cycle the computer without properly shutting down; for instance, by using the
	  reset or power switch.
	
	5. When computer restarts, open Visual FoxPro 6.0 SP3 or later and attempt to
	  modify the form. The problem described in the "Symptoms" section may appear.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbvfp600bug kbGrpDSFox kbDSupport kbvfp700fix 
	Technology        : kbVFPsearch kbAudDeveloper
	Version           : :6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
