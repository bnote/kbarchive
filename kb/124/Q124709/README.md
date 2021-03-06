---
layout: page
title: "Q124709: PATCH: Out of Memory Error w/ AddNew/Update on Dynaset/Table"
permalink: /kb/124/Q124709/
---

## Q124709: PATCH: Out of Memory Error w/ AddNew/Update on Dynaset/Table

{% raw %}

	Article: Q124709
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 3.0
	Operating System(s): 
	Keyword(s): kbpatchkbbuglist kbfixlist
	Last Modified: 02-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Performing an AddNew and then and Update method on a table or dynaset causes the
	Jet database engine to allocate a small amount of memory that is not released
	until the Jet database engine is unloaded from memory. Therefore, programs that
	perform many Updates over a long period of time without unloading the Jet
	database engine will eventually result in an "Out of Memory" error.
	
	RESOLUTION
	==========
	
	There are two possible workarounds:
	
	
	Update Vbdb300.dll to version 3.00.0530, dated 1 Feb 95 by downloading
	Vbdb300.exe. You can find Vbdb300.exe, a self-extracting file, on these
	services: The following file is available for download from the Microsoft
	Download Center:
	
	  Vbdb300.exe
	  (http://download.microsoft.com/download/vb30/Patch/1/W9XNT4/EN-US/vbdb300.exe)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	  NOTE: This version of the Vbdb300.dll does require the VB/Access
	  compatibility layer (Comlyr.exe) and the updated Jet engine in the Access
	  Service Pack (Accsvc.exe in the GO MSACCESS forum).
	
	  DISCLAIMER: The version of Vbdb300.dll (hereinafter the "Product") is being
	  released as a patch (the "Patch") in order to fix a specific problem a few
	  customers are experiencing with Microsoft Visual Basic 3.0. This Patch has
	  been tested comprehensively to ensure that no errors or additional problems
	  are introduced into the Product during normal usage. However, in order to
	  release this Patch as quickly as possible, it has not have been subjected to
	  the same series of rigorous functional and regression tests that are used for
	  regular production products. Consequently, this Patch should be installed
	  only if you are experiencing the specific problem mentioned above, and not
	  applied indiscriminately. Use of this Patch is governed by all of the
	  provisions of the Microsoft End User Software License Agreement included with
	  the Product, as if it were the Product.
	
	  In addition, the Patch is provided to you at no additional charge. Microsoft
	  Corporation owns all right, title and interest in and to the Patch.
	
	  Copyright 1995 Microsoft Corporation, All Rights Reserved.
	
	-OR-
	
	Periodically shell to another Visual Basic program that does not use the Jet
	database engine to unload the database application. This will cause all of the
	memory held by the Jet database engine to be released back to the system. You
	can then restart your application from the non-database program.
	
	STATUS
	======
	
	This bug in Microsoft Visual Basic for Windows version 3.0 was corrected with
	Vbdb300.dll version 3.00.0530 dated 1 Feb 95.
	
	
	MORE INFORMATION
	================
	
	This problem is not corrected by using the Microsoft Access 2.0/Visual Basic 3.0
	Compatibility Layer; nor is it corrected by using the Microsoft Access version
	2.0 Service Pack.
	
	Steps to Reproduce Behavior
	---------------------------
	
	NOTE: You will need the older version 3.00.0529 of Vbdb300.dll and the
	Professional Edition of Visual Basic to reproduce the problem outlined below.
	
	1. Create a new project. Form1 is created by default.
	
	2. Add a label control to Form1.
	
	3. Enter the following code for Form1:
	
	     'Enter the following lines as one line
	
	     Declare Function GetFreeSpace Lib "kernel" (ByVal flag As Integer) _
	        As Long
	
	     Sub Form_Activate ()
	        Dim lngStartMem As Long
	        Dim lngUsedMem As Long
	        Dim lngRec As Long
	        Dim strMsg as String
	        Dim dbBiblio As Database
	        Dim dsAuthors As Dynaset
	
	        Label1.Caption = "Initializing..."
	        Label1.Refresh
	
	        Set dbBiblio = OpenDatabase("biblio.mdb")
	        Set dsAuthors = dbBiblio.CreateDynaset("Authors")
	        lngStartMem = GetFreeSpace(0)
	
	        BeginTrans
	        For lngRec = 1 To 100000
	           dsAuthors.AddNew
	           dsAuthors("Au_ID") = lngRec + 100
	           dsAuthors("Author") = "Doe, John"
	           dsAuthors.Update
	           If lngRec Mod 500  = 0 Then
	              CommitTrans
	              lngUsedMem = lngStartMem - GetFreeSpace(0)
	              strMsg = "Records: " & CStr(lngRec) & Chr$(13) & Chr$(10)
	              strMsg = strMsg & "Used: " & CStr(lngUsedMem)
	              Label1.Caption = strMsg
	              Label1.Refresh
	              BeginTrans
	           End If
	        Next
	        CommitTrans
	
	        dsAuthors.Close
	        dbBiblio.Close
	     End Sub
	
	4. Run the program. The "Used:" line of the label tells how much memory has been
	  allocated from the global memory heap. This memory is not recovered until you
	  exit from Visual Basic.
	
	Additional query words: 3.00 leak low adding comlyr accsvc
	
	======================================================================
	Keywords          : kbpatch kbbuglist kbfixlist
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB300Search kbVB300
	Version           : :3.0
	
	=============================================================================
	

{% endraw %}
