---
layout: page
title: "Q63235: FIX: L4050 Incorrectly Documented in Online Help"
permalink: /kb/063/Q63235/
---

## Q63235: FIX: L4050 Incorrectly Documented in Online Help

{% raw %}

	Article: Q63235
	Product(s): Microsoft Programming Utilities
	Version(s): MS-DOS:5.1
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 31-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft LINK for MS-DOS, version 5.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When linking a very small program with /EXEPACK, the Microsoft LINK utility
	version 5.1 sometimes gives the following error message:
	
	  LINK: warning L4050: file not suitable for /EXEPACK; relink without
	
	The online Help documentation returns the following incorrect information:
	
	  LINK warning L4050
	
	  too many public symbols for sorting
	
	  The linker uses the stack and all available memory in the near heap to sort
	  public symbols for the /MAP option. If the number of public symbols exceeds
	  the space available for them, this warning is issued and the symbols are not
	  sorted in the map file but are listed in an arbitrary order.
	
	  Reduce the number of symbols.
	
	RESOLUTION
	==========
	
	The correct documentation for this error (except the number) is as follows and
	can be found in the online Help under L1114:
	
	  Fatal LINK error L1114
	
	  file not suitable for /EXEPACK; relink without
	
	  For the linked program, the size of the packed load image plus packing
	  overhead was larger than that of the unpacked load image.
	
	  Relink without the /EXEPACK option.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem with the LINK utility version 5.1.
	This problem was corrected in the LINK utility version 5.13.
	
	MORE INFORMATION
	================
	
	Because of its noncritical nature, this error was changed from its previous
	status of a fatal error to a simple warning in LINK version 5.1. The warning
	associated with L4050 in earlier versions of LINK rarely appears in LINK 5.1;
	however, if it does, it will have the number L4070.
	
	Additional query words: 5.10
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbAudDeveloper kbZNotKeyword3 kbLINKSearch kbLINK510DOS
	Version           : MS-DOS:5.1
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
