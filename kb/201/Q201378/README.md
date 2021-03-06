---
layout: page
title: "Q201378: HOWTO: Remove a Virus From a File in Visual SourceSafe"
permalink: /kb/201/Q201378/
---

## Q201378: HOWTO: Remove a Virus From a File in Visual SourceSafe

{% raw %}

	Article: Q201378
	Product(s): Microsoft SourceSafe
	Version(s): WINDOWS:5.0,6.0
	Operating System(s): 
	Keyword(s): kbSSafe500 kbSSafe600 kbSSExplorer
	Last Modified: 01-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Your standard virus checker can be applied to the Visual SourceSafe data
	directory, and in most cases it finds viruses if they exist. Since Visual
	SourceSafe uses Reverse Deltas to recreate previous versions only, the last
	checked-in copy exists in its entirety. This could cause problems if a virus
	exists in an older version. The virus may not be recognizable to the virus
	checker since the complete "signature" of the virus may not be read.
	
	Depending on where in the history of the file the virus was introduced, some or
	all of the history may need to be removed. This ensures that no one gets an old,
	infected copy.
	
	MORE INFORMATION
	================
	
	The following provides a few scenarios of versions of a Visual SourceSafe file
	infected with a virus and recommended methods on how to clean them.
	
	1. If your case is:
	
	Version 6-Clean
	Version 5-Clean
	Version 4-Clean
	Version 3-Infected
	Version 2-Infected
	Version 1-Infected
	
	Use the Archive utility to remove versions 1-3. Be sure to store and/or name the
	archive file appropriately so that no one attempts to restore it.
	
	2. If your case is:
	
	Version 6-Infected
	Version 5-Infected
	Version 4-Infected
	Version 3-Infected
	Version 2-Clean
	Version 1-Clean
	
	You can use the rollback functionality from the Show History dialog box to
	destroy versions 3-6. Then check out (latest version is now 2), and copy over a
	cleaned version of 6, and then check it back in.
	
	3. If your case is:
	
	Version 6-Clean
	Version 5-Clean
	Version 4-Infected
	Version 3-Infected
	Version 2-Clean
	Version 1-Clean
	
	The best solution is to destroy and re-add the file back to Visual SourceSafe.
	But if you want to preserve the clean versions, you need to take a few extra
	steps. These versions do not have the same Time/Date stamps as they had
	originally and would be numbered versions 1,2, 3, and 4.
	
	First, do a Get on versions 5 and 6 to preserve the contents, and then follow the
	method described in Case #2. In the last part of that method, check out version
	2 and replace version 5 first, check it in, and then check it out again. Replace
	version 6, check it in, etc. This could be a time-consuming task if many more
	clean versions exist after the last infected version.
	
	REFERENCES
	==========
	
	Search "archiving" from the SSAdmin online help for more information regarding
	the Archive utility.
	
	Additional query words: kbDSupport
	
	======================================================================
	Keywords          : kbSSafe500 kbSSafe600 kbSSExplorer 
	Technology        : kbSSafeSearch kbAudDeveloper kbSSafe600 kbSSafe500
	Version           : WINDOWS:5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
