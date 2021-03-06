---
layout: page
title: "Q102083: FILE: Fw0844.exe FoxDoc Default Template Files"
permalink: /kb/102/Q102083/
---

## Q102083: FILE: Fw0844.exe FoxDoc Default Template Files

{% raw %}

	Article: Q102083
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:2.5,2.5a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 04-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Fw0844.exe is a file that with an Application Note that contains an updated
	version of FoxDoc that allows you to use different templates & the original
	template files, which you can modify.
	
	MORE INFORMATION
	================
	
	The following file is available for download from the Microsoft Software
	Library:
	
	  Fw0844.exe
	  (http://support.microsoft.com/download/support/mslfiles/Fw0844.exe)
	
	  For more information about downloading files from the Microsoft Software
	  Library, please see the following article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	
	The FoxDoc application uses default templates to generate printed documentation
	about FoxPro programs, applications, or entire projects. The disk included with
	the "FoxDoc Default Template Files" (FW0844) Application Note contains an
	updated version of FoxDoc that allows you to use different templates. This disk
	also contains the original template files, which you can modify and then use in
	FoxDoc to customize your printed documentation.
	
	THE TEXT OF FW0844
	
	======================================================================
	      Microsoft(R) Technical Support Application Note (Text File)
	                FW0844: FOXDOC DEFAULT TEMPLATE FILES
	======================================================================
	                                                  Revision Date: 7/93
	                                                      1 Disk Included
	
	The following information applies to Microsoft FoxPro(R) versions 2.5
	and 2.5a for Windows.
	
	----------------------------------------------------------------------
	| INFORMATION PROVIDED IN THIS DOCUMENT AND ANY SOFTWARE THAT MAY     |
	| ACCOMPANY THIS DOCUMENT (collectively referred to as an Application |
	| Note) IS PROVIDED "AS IS" WITHOUT WARRANTY OF ANY KIND, EITHER      |
	| EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE IMPLIED      |
	| WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A PARTICULAR       |
	| PURPOSE. The user assumes the entire risk as to the accuracy and    |
	| the use of this Application Note. This Application Note may be      |
	| copied and distributed subject to the following conditions:  1) All |
	| text must be copied without modification and all pages must be      |
	| included;  2) If software is included, all files on the disk(s)     |
	| must be copied without modification (the MS-DOS(R) utility          |
	| diskcopy is appropriate for this purpose);  3) All components of    |
	| this Application Note must be distributed together;  and  4) This   |
	| Application Note may not be distributed for profit.                 |
	|                                                                     |
	| Copyright (C) 1993 Microsoft Corporation.  All Rights Reserved.     |
	| Microsoft, FoxPro, and MS-DOS are registered trademarks and Windows |
	| is a trademark of Microsoft Corporation.                            |
	|---------------------------------------------------------------------
	
	INTRODUCTION
	============
	
	The FoxDoc application uses default templates to generate printed
	documentation about FoxPro programs, applications, or entire projects.
	These default templates are embedded in the Foxdoc.app file and are
	not available as separate files.
	
	The disk included with this Application Note contains an updated
	version of FoxDoc that allows you to use different templates. This
	disk also contains the original template files, which you can modify
	and then use in FoxDoc to customize your printed documentation.
	
	To install the templates and updated FoxDoc files
	-------------------------------------------------
	
	- Copy all the files from the enclosed FW0844 disk to your FOXPROW
	  directory.
	
	  For example, to copy the files from your floppy disk drive A to the
	  FOXPROW directory on drive C, type the following command at the
	  MS-DOS command prompt and press ENTER:
	
	     copy a:\*.* c:\foxprow
	
	HOW FOXDOC USES TEMPLATES
	=========================
	
	  NOTE: The terms "template" and "report" can be used interchangeably
	  in this document. The FoxDoc application and its dialog boxes refer
	  to "templates," which are actually FoxPro report files. You can
	  modify a FoxDoc template the same way you modify any other FoxPro
	  report.
	
	FoxDoc creates its reports by first reading a .prg or .doc file (which
	are text files) into a database, and then issuing a REPORT FORM
	command on the database. You cannot control how the text file is
	imported into the database, but you can modify the template used to
	print from the database. There are separate templates for source code
	files, action diagrams, documentation reports, and the table of
	contents.
	
	For example, the action diagram template would be used once for each
	action diagram file that FoxDoc produces. FoxDoc performs the
	following actions for each action diagram:
	
	1. Identifies the next action diagram.
	2. Imports it into a temporary database.
	3. Issues a REPORT FORM template_filename TO PRINT command to print
	  the action diagram using the appropriate action diagram report
	  template.
	4. Repeats from step 1, until all the action diagrams have been
	  printed. The template is "called" once for each action diagram
	  file.
	
	To specify the templates used by FoxDoc
	----------------------------------------
	
	To view the default templates, start FoxDoc. From the FoxDoc main
	dialog box, under Other Options, choose the Printing button, then the
	Templates button. The Printing Templates dialog box displays the list
	of templates used for the following:
	
	 Programs:               fdprg.frx
	 Action Diagrams:        fdact.frx
	 Documentation Reports:  fddoc.frx
	 Table of Contents:      fdtoc.frx
	
	To use a different template, choose the appropriate button, select the
	desired template (.FRX file) from the Open dialog box, then choose the
	Open button. FoxDoc will now use that template to print your
	documentation.
	
	Tips on Modifying the FoxDoc Templates
	--------------------------------------
	
	When creating or modifying a FoxDoc template, you can use the
	following fields:
	
	Field name           Description
	---------------------------------------------------------------------
	
	fd_name:             The name of the current file that is being
	                     printed
	fd_sysname:          The name of the application system that is being
	                     documented and printed (taken from first FoxDoc
	                     screen)
	fd_author:           The system author (taken from first FoxDoc
	                     screen)
	fd_copyrightdate:    The copyright date (taken from first FoxDoc
	                     screen)
	fd_holder:           The copyright holder (taken from first FoxDoc
	                     screen)
	fd_reporttime:       The time that the first report was printed (so
	                     that all reports from a single documentation
	                     session can have the same date and time)
	line:                A single line from the file that is being
	                     printed
	
	Typically, the detail band of the report template contains only the
	line field and nothing else.
	
	In addition, FoxPro system variables (for example, _PAGENO) can be
	used. The best way to see how these are used is to study the existing
	templates, which use many of these variables.
	
	MORE INFORMATION ABOUT THE UPDATED FOXDOC FILES
	===============================================
	
	The FoxDoc files supplied with this Application Note (Foxdoc.app,
	Foxdoc.fll, and Foxdoc.msg) are the same files included with FoxPro
	2.5a for Windows. These files correct a problem with selecting
	alternative template files in the FoxDoc application in FoxPro 2.5 for
	Windows. In the Printing Templates dialog box (under Other Options
	select the Printing button, then the Templates button) in FoxDoc 2.5,
	the template file used for each item is listed in the adjacent text
	box. When you try to select a different template file by choosing the
	appropriate button under Report Form Templates For and then selecting
	a template file from the Open dialog box, the FoxDoc template file in
	the text box reverts to the default file instead of being replaced by
	the file that you just selected.
	
	REFERENCES
	==========
	
	Developer's Guide, Chapter 15 pages D15-27.
	
	Additional query words: FoxWin 2.50 softlib appnote
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbFoxproSearch kbFoxPro250 kbFoxPro250a
	Version           : WINDOWS:2.5,2.5a
	
	=============================================================================
	

{% endraw %}
