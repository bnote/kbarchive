---
layout: page
title: "Q108918: WD97: Err Msg: &quot;Cannot Save or Create File&quot; to Network Drive"
permalink: /kb/108/Q108918/
---

## Q108918: WD97: Err Msg: &quot;Cannot Save or Create File&quot; to Network Drive

{% raw %}

	Article: Q108918
	Product(s): Word 97 for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbnetwork kbsetup word97kbfaq
	Last Modified: 07-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you save a file to a network drive in Word Document format, the following
	error message may occur in Word for Windows:
	
	  Word cannot save or create this file. Make sure the disk is not full or write
	  protected. <path><filename>
	
	  -or-
	
	  Word cannot save or create this file. The disk may be full or
	  write-protected. Try one or more of the following:
	  *Free more memory.
	  *Make sure that the disk you want to save the file on is not full,
	  write-protected, or damaged.
	
	NOTE: Sometimes you can save the file the first time to a network drive, but the
	error occurs when you try to save the file a second time.
	
	Similarly, when you open a Word for Windows document from a network drive, the
	following error message may occur:
	
	  Cannot open document.
	
	These errors do not occur if you save the file to your local hard disk or floppy
	disk drive. Similarly, the error does not occur if you save the file to a
	network drive in a file format other than Word Document format, such as Word For
	Windows 2.0 format or RTF (Rich Text Format).
	
	These errors occur when you use Windows 95 if you use a real-mode network
	protocol instead of the normal Windows 95 network drivers.
	
	CAUSE
	=====
	
	You cannot save Word documents on a network drive if your network operating
	system file-sharing and file-locking capabilities are not turned on or are set
	too low.
	
	
	You can save in other file formats on a network drive because the file converters
	do not use the Storage.dll file, which requires file-locking capabilities.
	
	RESOLUTION
	==========
	
	To avoid these error messages, have your network administrator turn on or
	increase the range-locking settings for your network.
	
	For more information about the file-sharing and file-locking capabilities of your
	network, refer to your network documentation.
	
	To temporarily work around this "Cannot save or create file" problem, do one of
	the following:
	
	- Save your document to a local hard disk or floppy disk. -or-
	
	- Save the document on the network drive in a different file format, such as
	  Word For Windows 2.0.
	
	- Save the file to the local hard drive and move it to the network drive. You
	  will also need to have your network administrator remove this file if nobody
	  is using it.
	
	Additional query words: lantastic unix TotalNet sharing control wollongong w_works winworks
	
	======================================================================
	Keywords          : kbnetwork kbsetup word97 kbfaq
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
