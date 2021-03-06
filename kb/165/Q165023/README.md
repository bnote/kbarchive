---
layout: page
title: "Q165023: SNA Server Issues with DBCS 3270 Printing"
permalink: /kb/165/Q165023/
---

## Q165023: SNA Server Issues with DBCS 3270 Printing

{% raw %}

	Article: Q165023
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, version 3.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	This article only applies to double byte character set (DBCS) code pages. DBCS
	code pages include:
	
	  290 Japanese (Katakana)
	  930 Japanese (Extend Katakana)
	  931 Japanese (English-lower)
	  933 Korean
	  935 Chinese (PRC)
	  937 Chinese (Taiwan)
	  939 Japanese (Extend English)
	
	1. DBCS Characters Incorrect and Multiple Sessions Fail.
	
	
	  SYMPTOMS
	
	  DBCS characters do not print correctly in both LU1 and LU3 datastreams, and a
	  Dr. Watson log is generated whenever multiple print sessions are activated.
	
	   - DBCS characters are not printed correctly in LU3. ShiftOut(0x0E) and
	     ShiftIn(0x0F) are not handled correctly. These codes mark the beginning
	     and end of DBCS data. Because these codes are not recognized, DBCS
	     characters between SO(0x0E) and SI(0x0F) are printed as two single byte
	     character set (SBCS) characters.
	
	   - Dr.Watson errors appear on activations of multiple printer sessions. If
	     only one DBCS code page session is activated, the problem does not occur.
	     However, if two or more DBCS code page sessions are activated, a Dr.
	     Watson error occurs.
	
	   - DBCS characters are not printed correctly in LU1. If DBCS data containing
	     one or more control codes (NL, CR, LF, BS, and so on) is sent, the DBCS
	     data is printed incorrectly.
	
	  RESOLUTION
	
	  To resolve these problems, obtain the hotfix mentioned in the STATUS section
	  of this article.
	
	
	2. Multiple Fixes for DBCS SCS Printing.
	
	  SYMPTOMS
	
	  There were multiple problems found in DBCS SCS printing. The following
	  problems were reported:
	
	  a. When the margin is set in the Printing tab of the Printer Session
	     Properties Printing tab, the position of the grid line is incorrect.
	
	  b. The grid line is incorrect on some control codes.
	
	  c. The automatic line feed (LF) is not performed. This automatic LF is a
	     special function for the grid handling (for DBCS code page only).
	
	  d. "-R" is not returned on incomplete Set Attribute (SA) Datastreams.
	
	        Complete SA format:
	           DBCS: 0x'2843xx'
	           Grid: 0x'28C2xx'
	        Incomplete SA:
	           The data chain ends with 0x'28' or 0x'2843' or 0x'28C2'.
	
	  e. New line (NL) is not performed after Maximum Presentation Position (MPP).
	
	  f. NUL control code is printed.
	
	  STEPS
	
	  To resolve these problems, obtain the hotfix mentioned in the STATUS section
	  of this article. With the hotfix:
	
	  a. The printing position of the grid was adjusted for the margin.
	
	  b. The grid handling after some control codes(NL, CR, LF, BS, and so on) was
	     modified.
	
	  c. The automatic LF process for the grid has been corrected.
	
	  d. For the incomplete SA format, -R is set at the end of the data chain.
	
	  e. The NL process for MPP has been corrected.
	
	  f. The NUL character was translated to space.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server version 3.0. This
	problem was corrected in the latest Microsoft SNA Server 3.0 U.S. Service Pack.
	For information on obtaining the service pack, query on the following word in
	the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	Additional query words: prodsna
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300
	Version           : WINDOWS:3.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
