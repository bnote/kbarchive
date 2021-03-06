---
layout: page
title: "Q176909: HOWTO: Move a VSS Database or Project to New Location"
permalink: /kb/176/Q176909/
---

## Q176909: HOWTO: Move a VSS Database or Project to New Location

{% raw %}

	Article: Q176909
	Product(s): Microsoft SourceSafe
	Version(s): WINDOWS:4.0,4.0a,5.0,6.0
	Operating System(s): 
	Keyword(s): kbSSafe400 kbSSafe500 kbSSafe600 kbFAQ kbSsafe600FAQ
	Last Modified: 18-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, versions 5.0, 6.0 
	- Microsoft Visual SourceSafe, 16-bit, for Windows, version 4.0 
	- Microsoft Visual SourceSafe, 32-bit, for Windows 4.0 
	- Microsoft Visual SourceSafe, 16-bit, for Windows, version 4.0a 
	- Microsoft Visual SourceSafe, 32-bit, for Windows 4.0a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes three common scenarios for moving Visual SourceSafe
	projects or databases to a new location. The steps necessary to successfully
	accomplish this are detailed in the MORE INFORMATION section below.
	
	Scenario 1
	----------
	
	Moving the entire Visual SourceSafe server installation from one machine to
	another.
	
	Scenario 2
	----------
	
	Moving a project or projects from one database to another, while preserving the
	project's history.
	
	Scenario 3
	----------
	
	Moving only the DATA directory to a machine other than the Visual SourceSafe
	server. This scenario eliminates the need to modify clients accessing the
	database.
	
	IMPORTANT: Whichever method you use, make sure to do a full backup of your data
	first.
	
	MORE INFORMATION
	================
	
	The procedures within each scenario may vary depending on the version of Visual
	SourceSafe you are running.
	
	Scenario 1
	----------
	
	Moving the entire VSS server installation from one machine to another.
	
	1. Copy the entire <server>\VSS installation directory to the new server
	  location.
	
	2. Make sure that the Visual SourceSafe clients can still access the data from
	  the new location.
	
	3. Step 3 varies according to what version of Visual SourceSafe you are using:
	
	  For Visual SourceSafe 4.x clients:
	
	  a. Locate the local copy of the Srcsafe.ini file (for example, <local
	     drive>\vssclient\Srcsafe.ini) and open it in a text editor.
	
	  b. Edit the line containing the #include statement so that it points to the
	     new location of the server's Srcsafe.ini. For example:
	
	     Change:
	
	  #include \\oldserver\oldshare\vss\srcsafe.ini
	
	     To:
	
	  #include \\newserver\newshare\vss\srcsafe.ini
	
	  For Visual SourceSafe 5.x or later clients:
	
	  a. Open the Visual SourceSafe Explorer. Click OK if you get the following
	     error:
	
	  File '\\oldserver\oldshare\srcsafe.ini' not found.
	
	  b. From the Visual SourceSafe Login dialog box, click Browse.
	
	  c. Click Browse from the Open SourceSafe Database dialog box.
	
	  d. Type in the UNC path to the new location of the Visual SourceSafe server
	     directory and open the srcsafe.ini. This will add a new entry in the
	     Available Databases list for the newly located database.
	
	  e. The old database reference can now be removed from this dialog box.
	
	IMPORTANT: Be sure to add the correct operating system level privileges to the
	new server directory.
	
	For additional information about required network privileges, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q131022 INFO: Required Network Rights for the SourceSafe Directories
	
	NOTE: If you have any shortcuts to this database, be sure to modify the shortcut
	Target on the client that pointed to ssadmin.exe on the old server.
	
	Scenario 2
	----------
	
	Moving a project or projects from one database to another, while preserving the
	project's history.
	
	NOTE: This process is for Visual SourceSafe 5.0 or greater only.
	
	Use the SSARC and SSRESTOR utilities included in Visual SourceSafe 5.0. With
	these utilities, you can archive projects, preserve their histories, and restore
	them to a new database.
	
	NOTE: You must have SourceSafe Admin privileges to use these utilities. For more
	information on the use of SSARC and SSRESTORE, see the Visual SourceSafe,
	version 5.0, "Visual SourceSafe User's Guide," Appendix B, pages 216-220 or
	under the SSAdmin Online Help topic "Basic Administrator Operations".
	
	NOTE: In order to restore a project successfully your archive must include the
	latest versions all the files in the project. If you use the -v switch with
	SSARC to archive off earlier versions of your files, you will not be able to
	restore that archive to a different database because it needs the later
	versions.
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q173387 PRB: Restoring an Archive of an Entire Database
	
	
	
	NOTE: Because the physical file names get renamed when you restore a project to a
	new database, it may be necessary to reconnect projects that are integrated with
	Visual SourceSafe. Please refer to the following article in the Microsoft
	Knowledge Base for additional information:
	
	  Q166305 HOWTO: Reconnecting a Visual C++ Project to Source Control
	
	Scenario 3
	----------
	
	Moving only the DATA directory to a machine other than the Visual SourceSafe
	server:
	
	1. Copy only the <VSS server>\DATA directory to its new location.
	
	2. Edit the <VSS server>\srcsafe.ini file's data_path variable. For
	  example:
	
	  Change:
	
	  data_path = data
	
	  To:
	
	  data_path = \\<new server path>\data
	
	Clients accessing this database do not need to be modified since the server's
	Srcsafe.ini has not moved.
	
	Additional Tips
	---------------
	
	1. Remove permissions for all users at the operating system level for the old
	  Visual SourceSafe installation to prevent them from checking their work in
	  and out of the wrong database.
	
	2. Once you are confident that the process is complete, delete the old Visual
	  SourceSafe installation.
	
	3. If there are shadow folders, journal files, or web deploy locations set up in
	  the old installation, you need to make sure that all the paths correctly
	  reference the new server location. These settings are in the srcsafe.ini file
	  on the server copy of Visual SourceSafe.
	
	4. When you start Visual SourceSafe from a client install, you might see the
	  following errors:
	
	  Invalid DOS path: "<path>\scrsafe.ini"
	
	  Indicates an incorrect path in the #include line of the client's srcsafe.ini.
	
	-or-
	
	  Invalid filename: "<path>\scrsafe.ini"
	
	Indicates insufficient operating system rights.
	
	REFERENCES
	==========
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q175950 HOWTO: Change the Name of a Visual SourceSafe Database
	
	Additional query words: relocate
	
	======================================================================
	Keywords          : kbSSafe400 kbSSafe500 kbSSafe600 kbFAQ kbSsafe600FAQ 
	Technology        : kbSSafeSearch kbAudDeveloper kbSSafe600 kbSSafe400 kbSSafe400a kbSSafe500 kbSSafe16bitSearch kbSSafe32bitSearch
	Version           : WINDOWS:4.0,4.0a,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
