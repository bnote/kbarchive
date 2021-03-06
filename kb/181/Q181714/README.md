---
layout: page
title: "Q181714: Err Msg: The Initialization Values for MSDN Archive Edition..."
permalink: /kb/181/Q181714/
---

## Q181714: Err Msg: The Initialization Values for MSDN Archive Edition...

{% raw %}

	Article: Q181714
	Product(s): Microsoft Home Multimedia Titles
	Version(s): ; WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbsetup kbimu
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Developer Network Library Archive 
	- the operating system: Microsoft Windows versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to start Microsoft Developer Network (MSDN) Library Archive on
	a computer running Microsoft Windows 3.1x, you receive the following error
	message:
	
	  Microsoft InfoViewer
	
	  The initialization values for MSDN Archive Edition are not correct in your
	  Infoview.ini file. Please run Setup or read the manual setup instructions.
	
	CAUSE
	=====
	
	This behavior occurs because the 16-bit installation program writes incorrect
	information to the Infoview.ini file.
	
	RESOLUTION
	==========
	
	To resolve this issue, follow these steps:
	
	1. If you want to use only the MSDN Library Archive, skip to step 2. If you want
	  to use both the MSDN Library Archive and the MSDN January 97 Library, install
	  the MSDN January 97 Library. To do so, follow these steps:
	  a. Insert the MSDN January 97 Library CD-ROM into the CD-ROM drive.
	
	  b. In Program Manager, click File, and then click Run.
	
	  c. In the Command Line box, type the following line, and then click OK
	
	  "<drive>:\Setup.exe" (without the quotation marks)
	
	     where <drive> is the letter of the CD-ROM drive.
	
	  d. Follow the instructions on the screen to install the MSDN January 97
	     Library.
	
	2. Install the MSDN Library Archive. To do so, follow these steps:
	  a. Insert the MSDN Library Archive CD-ROM into the CD-ROM drive.
	
	  b. In Program Manager, click File, and then click Run.
	
	  c. In the Command Line box, type the following line, and then click OK
	
	  "<drive>:\Setup.exe" (without the quotation marks)
	
	     where <drive> is the letter of the CD-ROM drive.
	
	  d. Follow the instructions on the screen to install the MSDN Library Archive.
	
	3. Use a text editor such as Notepad to open the Infoview.ini file, located in
	  the Windows folder.
	
	4. Add the following lines to the [MSDNarc.Settings] section:
	
	  licensed.name=Your Name
	  licensed.organization=Your Organization
	  license_version=01/28/97
	  license_last_read=11/09/95
	
	5. Verify that the following lines are present in the [series] section:
	
	        MSDN=msdncd18.MVB
	        MSDNcdc=MSDNcdc.MVB
	
	6. Verify that the following lines are present in the [all titles] section:
	
	        MSDNcdc.MVB=MSDNcdc.MVB
	        msdncd18.MVB=msdncd18.MVB
	
	7. On the File menu, click Save.
	
	8. On the File menu, click Exit.
	
	9. Copy the Relnotes.hlp file and the License.hlp file from the MSDN Library
	  Archive CD-ROM to the folder where the MSDN Library Archive is installed. By
	  default, the MSDN Library Archive is installed to the following location:
	
	     C:\Msdn\Archive
	
	  For more information about how to copy a file in Windows, please refer to your
	  Windows printed documentation or online Help.
	
	Additional query words: multi multi-media media mm win3x devnet lib arc
	
	======================================================================
	Keywords          : kbenv kberrmsg kbsetup kbimu 
	Technology        : kbOSWinSearch kbZNotKeyword6 kbMSDNSearch kbZNotKeyword2 kbOSWin310 kbOSWin311
	Version           : :; WINDOWS:3.1,3.11
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
