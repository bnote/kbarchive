---
layout: page
title: "Q109613: How to Run Another Application from FoxPro for Macintosh"
permalink: /kb/109/Q109613/
---

## Q109613: How to Run Another Application from FoxPro for Macintosh

{% raw %}

	Article: Q109613
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:2.5b,3.0b
	Operating System(s): 
	Keyword(s): kbcode kberrmsg
	Last Modified: 05-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FoxPro for Macintosh, version 2.5b 
	- Microsoft Visual FoxPro for Macintosh, version 3.0b 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	Although the RUN command can be used to launch other programs from FoxPro on the
	MS-DOS and Windows platforms, in FoxPro for Macintosh, the "Feature Not
	Available" error message is generated when the RUN command is used.
	
	To launch another application from FoxPro for Macintosh, use the RUNSCRIPT
	command to execute an AppleScript that contains a scripting command to launch
	the desired application.
	
	MORE INFORMATION
	================
	
	AppleScript is an extension available for Macintosh system software release 7.0x
	that adds functionality to the Macintosh operating system by providing a
	standard protocol for communication between applications. It is part of Apple's
	Open Scripting Architecture.
	
	Because FoxPro for Macintosh is AppleScript aware, it can run prewritten scripts
	using the RUNSCRIPT command. The syntax of the RUNSCRIPT command can be found in
	the FoxPro for Macintosh "Language Reference" and in the online help file.
	
	To launch an application using AppleScript, the application must be Apple-
	event-aware and support the open application ("oapp") Apple Event. An Apple
	event is a high-level message that is passed from one application to another,
	including the operating system. Most applications, especially those written or
	updated since System 7 was released, support the basic high-level events; the
	open application event is one of these.
	
	The sample scripts below show two methods, one interactive and one
	noninteractive, that can be used to launch another Macintosh application. To use
	these scripts, type them into the AppleScript Editor, save them, and then run
	them from Microsoft FoxPro for Macintosh using the RUNSCRIPT command.
	
	NOTE: Double hyphens represent comments to the AppleScript interpreter. Due to
	the limitations of the character set used to print this article, the
	command-continuation character produced by pressing OPTION+RETURN on the Apple
	keyboard has been replaced by a semicolon (;). Scripting commands are broken
	into multiple lines for readability only.
	
	Interactive Sample Script
	-------------------------
	
	The following script is interactive, allowing the user to choose the application
	to run from a standard Macintosh Open dialog box. Only "APPL" (application) type
	files are displayed. The chosen application is stored to the variable
	"appToRun." An error handler surrounds the code. If the user clicks Cancel in
	the "choose file" Open dialog box, the error number -128 is returned. Otherwise,
	the null string is returned. The FoxPro program that invokes the script should
	handle the return value appropriately.
	
	NOTE: This script sample uses "choose file", a scripting addition provided with
	the AppleScript extension and stored in the Scripting Additions folder in the
	System Folder:Extensions folder. If "choose file" is not available, this script
	will produce an error.
	
	    -- script to run another Macintosh application
	    try
	       set appToRun to ;
	          ((choose file of type {"APPL"}) as string)
	       tell application appToRun to run
	       return ""
	    on error errText number errNum
	       return errNum
	    end try
	
	Save the script with the name RunApp. To run the script, issue the following
	command in the FoxPro Command window or from within a FoxPro program:
	
	    RUNSCRIPT "Macintosh HD:Scripts:RunApp" TO retVal
	
	"retVal" contains the value returned from the script--either the null string or
	an error number.
	
	Noninteractive Script Sample
	----------------------------
	
	If you don't need an interactive script, you can use the following script to
	launch an application by hard-coding its name into the script; in the following
	sample, the application is Microsoft Excel:
	
	    tell application "Macintosh HD:Apps:Excel 4.0:Microsoft Excel" to run
	
	NOTE: Remember to replace the pathname to the application as necessary.
	
	
	REFERENCES
	==========
	
	For more information about Apple events and AppleScript, contact the Apple
	Programmer's and Developer's Association (APDA). The following references are
	also available:
	
	  "Inside Macintosh: Interapplication Communication," Apple Computer,
	  Addison-Wesley Publishing Company, 1993
	
	  "AppleScript Developer Toolkit," Apple Computer, 1993
	
	  Microsoft FoxPro for Macintosh "Language Reference"
	
	Additional query words: VFoxMac FoxMac
	
	======================================================================
	Keywords          : kbcode kberrmsg 
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbFoxproSearch kbFoxPro250bMac kbVFP300bMac
	Version           : MACINTOSH:2.5b,3.0b
	
	=============================================================================
	

{% endraw %}
