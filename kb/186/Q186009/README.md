---
layout: page
title: "Q186009: PRB: Errors Starting the Coverage Profiler"
permalink: /kb/186/Q186009/
---

## Q186009: PRB: Errors Starting the Coverage Profiler

{% raw %}

	Article: Q186009
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When starting the Coverage Profiler application, the following error message
	occurs:
	
	  OLE error code 0x.
	
	CAUSE
	=====
	
	The Comdlg32.ocx is not present or is an incompatible version for use with the
	Coverage Profiler.
	
	RESOLUTION
	==========
	
	Listed below are three possible resolutions to this problem.
	
	- Obtain the correct version of the Comdlg32.ocx and make sure it is installed
	  in the \Windows\System or \Winnt\System32 directory, as appropriate.
	
	  -or-
	
	- Choose Ignore and OK in the error messages. The Visual FoxPro GETFILE()
	  dialog box appears allowing a log file to be opened.
	
	  -or-
	
	- Modify the Coverage Profiler application so it does not use the Comdlg32.ocx.
	  The following steps can be used to modify the Coverage.app:
	
	  1. Unzip the XSource.zip file found in the \VFP6\Tools\XSource folder. If the
	     Winzip option to Use Folder Names is used, a Coverage directory, along
	     with other folders, is created that contains the Coverage Profiler source
	     files.
	
	  2. Open the Coverage.pjx project.
	
	  3. Go to the Other tab and expand the Text Files node. Find the COV_TUNE file
	     and modify the file.
	
	  4. In the COV_TUNE.h file, find the # DEFINE COV_USE_OCXS .T. line. Change
	     the .T. to .F. then save and close the COV_TUNE.h file.
	
	  5. Rebuild the Coverage.app application. Be sure to save the application in
	     the Visual FoxPro 6.0 folder or point the _Coverage system memory variable
	     to the location of the rebuilt Coverage.app.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	The Coverage Profiler is a new tool in Visual FoxPro 6.0 that provides
	information about the lines of code run in a program. The Coverage Profiler
	writes a log file. Issuing the SET COVERAGE TO "somefile.log" command when a
	program or form runs creates a log file. You access the Coverage Profiler
	application to analyze the log file from the Visual Foxpro Tools menu. However,
	there are other ways to start the Coverage Profiler application.
	
	When the Coverage Profiler application starts, if a log file has not specified,
	the Open dialog box appears prompting for the name of the log file to open. The
	Open dialog box comes from the Comdlg32.ocx and installs with Visual FoxPro.
	
	If, for some reason, the Comdlg32.ocx is missing or is an incompatible version, a
	series of error messages occur. Below is a list of the error messages that
	occur. Errors 2, 3 and 4 appear when you select Ignore in the first error
	message.
	
	Error 1:
	
	  Program Error
	  OLE error code 0x.
	  <Cancel> <Suspend> <Ignore> <Help>
	
	Error 2:
	
	  Coverage Profiler Problem
	  Problem:
	  Property CDLCOV_GETFILE is not found.
	  getresourcelocation
	  <OK>
	
	Error 3:
	
	  Coverage Profiler Problem
	  Problem:
	  Expression is not valid outside of WITH/ENDWITH.
	  getresourcelocation
	  <OK>
	
	Error 4:
	
	  Coverage Profiler Problem
	  Problem:
	  WITH/ENDWITH mismatch.
	  getresourcelocation
	  <OK>
	
	After choosing Ignore to the first error and then OK on all the others, a dialog
	box appears asking what log file to open. This dialog box is based on the Visual
	FoxPro GETFILE() function rather than the Comdlg32.ocx.
	
	Steps to Reproduce Behavior
	---------------------------
	
	To receive the error messages shown above, follow the steps below:
	
	1. Go to the \Windows\System or \Winnt\System32 folder, as appropriate for the
	  operating system and copy the Comdlg32.ocx to another folder. Once the
	  Comdlg32.ocx is safely backed up in another location, delete the copy in the
	  \Windows\System(32) directory.
	
	2. From the Tools menu in Visual FoxPro, choose the Coverage Profiler command.
	  The error messages listed above should appear. Choose Ignore on the first one
	  error.
	
	REFERENCES
	==========
	
	Visual FoxPro Books Online: Chapter 32: Application Development and Developer
	Productivity; Coverage Profiler Application
	
	Additional query words: FxenvError FxtoolGeneral kbvfp600
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : WINDOWS:6.0
	Issue type        : kbprb
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
