---
layout: page
title: "Q161980: Windows NT 4.0 Workstation Starts Here: Contents of Readme.wri"
permalink: /kb/161/Q161980/
---

## Q161980: Windows NT 4.0 Workstation Starts Here: Contents of Readme.wri

{% raw %}

	Article: Q161980
	Product(s): Microsoft Home Multimedia Titles
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 07-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following article contains a copy of the complete text of the Readme.wri
	file that comes with version 1.0 of Microsoft Windows NT Workstation 4.0 Starts
	Here.
	
	MORE INFORMATION
	================
	
	Readme.wri File
	---------------
	
	Microsoft(R) Windows NT(R) Workstation 4.0 Starts Here(TM)
	Version 4.0 Readme.wri
	
	Microsoft Windows NT Workstation 4.0 Starts Here is an interactive
	multimedia training tool that provides just-in-time training for
	Microsoft Windows NT Workstation, combining the best of proven
	learning techniques from print-based, video-based, and instructor-led
	training methods. Starts Here helps upgraders and new users master
	Windows NT Workstation 4.0 as quickly and easily as possible.
	
	System Requirements:
	--------------------
	
	Multimedia PC with a 486/33DX or higher processor
	Microsoft Windows NT Workstation Version 4.0 (16 MB RAM)
	12 MB of available hard disk space
	Double-speed CD-ROM drive
	Super VGA display with 256 colors or better
	Microsoft Mouse or compatible pointing device
	Windows NT-compatible sound board and headphones or speakers
	
	Microsoft Windows NT Workstation 4.0 Installation Tips:
	-------------------------------------------------------
	
	Starts Here assumes that Microsoft Windows NT Workstation 4.0 is
	properly installed on your computer.  Here are some things to check
	to ensure that Starts Here will function properly:
	
	Users have at least minimum User privileges.
	One lesson requires Power User privileges.
	
	If you need to print the lessons/documents, you must be connected
	to a printer. You may notice improper page layout on some dot matrix
	printers.
	
	Setup:
	------
	
	Autorun may not work on some CD changers.
	After Starts Here is installed, ActiveMovie(TM) is automatically
	installed.
	Administrator privileges are required for setup on
	Windows NT.
	The maximum path length for installation is 57 characters.
	
	Re-install option:
	------------------
	
	Problem:
	
	The re-install option in setup may be unable to repair a damaged
	installation.
	
	Workaround:
	
	1. Remove the damaged installation by running setup from the Starts
	  Here CD-ROM.  Select the Remove All option.
	2. Re-run setup from the Starts Here CD-ROM to create a new
	  installation.
	
	Palette Flashes:
	----------------
	
	Problem:
	
	Some videos may cause palette flashes on systems using a 256-color
	display mode.
	
	Workaround:
	
	1. Change to high color (16 bit/65536 colors) or higher, or
	  Remove the desktop background bitmap.
	
	Banyan Vines Client for Windows NT 4.0 Users:
	---------------------------------------------
	
	*** Network installations may fail due to a problem resolving UNC
	path names. ***
	
	Problem #1:
	An error dialog appears that says that ActiveMovie needs to be installed.
	Introduction and lesson videos will not play.
	
	Workaround:
	
	ActiveMovie can be installed manually using the following steps:
	
	1. In Windows NT Explorer or from the command prompt, open the
	  network path to the Starts Here setup location.
	2. Open the folder \System.
	3. Run Amovie.exe.
	
	Problem #2:
	
	Error message on startup: "Either the CD-ROM or your Network is not
	available...." The Registry, by default, stores the Media Path as a UNC
	\\server\share. The Banyan client for Windows NT 4.0 may be unable to
	resolve this.
	
	Workaround:
	
	1. Map a drive letter to the UNC \\server\share.
	2. From the Start Menu, run Regedit.
	3. Open this pathway:
	  "My Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft NT
	  Workstation 4.0 Starts Here".
	4. Double-click on the key field: "MediaPath".
	5. In the "Value Data" field substitute the new drive letter for the
	  \\server\share portion of the entry.
	
	Support:
	--------
	
	No-charge phone support is available via a toll call Monday through
	Friday, excluding holidays, 6:00AM to 6:00PM, Pacific Time. Call
	(206) 635-7033. Outside of the United States and Canada, contact the
	office of your local Microsoft subsidiary.
	
	Updated support information is also available via the Internet at
	the following World Wide Web address:
	
	  http://www.microsoft.com/mspress/support/ 
	
	Visit Microsoft on the Web:
	---------------------------
	
	http://www.microsoft.com - The Microsoft Corporation Home Page
	http://www.microsoft.com/mspress - The Microsoft Press Home Page
	http://www.microsoft.com/ntworkstation - The Microsoft Windows NT
	Workstation Home Page
	
	*** Beta Users ***
	------------------
	
	You must completely uninstall any Beta versions of Microsoft Windows
	NT Workstation 4.0 Starts Here before using the release version. To
	remove a Beta version from your computer:
	
	1. In the Control Panel, double-click Add/Remove Programs.
	2. On the Install/Uninstall tab, select Microsoft Windows NT
	  Workstation 4.0 Starts Here, then click Add/Remove.
	3. Follow the dialog boxes to remove Starts Here.
	4. From the Start menu, select Find, then select Files or Folders.
	5. In the Find: All Files box, type Ntw40sh in the Named: field, and
	  click Find Now.
	6. If the folder Ntw40sh is found, select the folder, then press
	  DELETE.
	
	You are now ready to install the release version.
	
	Microsoft Windows NT Workstation 4.0 Starts Here
	
	The names of companies, products, people, characters, and/or data
	mentioned herein are fictitious and are in no way intended to represent
	any real individual, company, product, or event, unless otherwise noted.
	
	Copyright (c)1997 Microsoft Press. All rights reserved.
	
	ISBN: 1-57231-522-9
	
	Additional query words: 1.0 multi media multimedia multi-media mmtitles kbmm starts here
	
	======================================================================
	Keywords          :  
	Version           : 1.0
	
	=============================================================================
	

{% endraw %}
