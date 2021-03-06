---
layout: page
title: "Q163490: WD97: How to Rename, Copy, or Delete a Macro"
permalink: /kb/163/Q163490/
---

## Q163490: WD97: How to Rename, Copy, or Delete a Macro

{% raw %}

	Article: Q163490
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbProgramming kbualink97 word8 kbwordvba word97
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	In earlier versions of Word for Windows, you can rename, copy, or delete a macro
	using the Organizer. In Word 97 for Windows and later, Visual Basic for
	Applications project modules can also be copied, renamed, or deleted using the
	Organizer.
	
	However, individual macros or procedures stored within a module must be operated
	on from either the Macros dialog box or from within the Visual Basic Editor.
	
	MORE INFORMATION
	================
	
	Microsoft provides programming examples for illustration only, without warranty
	either expressed or implied, including, but not limited to, the implied
	warranties of merchantability and/or fitness for a particular purpose. This
	article assumes that you are familiar with the programming language being
	demonstrated and the tools used to create and debug procedures. Microsoft
	support professionals can help explain the functionality of a particular
	procedure, but they will not modify these examples to provide added
	functionality or construct procedures to meet your specific needs. If you have
	limited programming experience, you may want to contact a Microsoft Certified
	Partner or the Microsoft fee-based consulting line at (800) 936-5200. For more
	information about Microsoft Certified Partners, please visit the following
	Microsoft Web site:
	
	  http://www.microsoft.com/partner/referral/
	
	For more information about the support options that are available and about how
	to contact Microsoft, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	Following are steps to perform these operations on macros stored within a project
	module.
	
	To Copy a Macro from One Module to Another
	------------------------------------------
	
	1. Make sure the templates or documents containing the projects to copy to and
	  from are currently open.
	
	2. On the Tools menu, point to Macro, and then click Macros.
	
	3. In the Macros In list, select the template or document containing the macro
	  you want to copy.
	
	4. In the list of available macros, select the macro to copy.
	
	5. Click Edit.
	
	6. In the Visual Basic Editor window, select the entire macro, including the Sub
	  and End Sub lines.
	
	7. On the Edit menu, click Copy.
	
	8. On the View menu, click Project Explorer.
	
	9. In the Project Explorer, open the project and the module that will contain
	  the copy of the macro.
	
	10. Click in the project's Module code window.
	
	11. In the Object list, click General.
	
	12. In the Procedure list, click Declarations.
	
	13. Position the insertion point on an empty line making sure it is below the
	  last line of code, if any, in the Declarations section.
	
	14. On the Edit menu, click Paste.
	
	15. On the File menu, click Save "<Project name>."
	
	16. On the File menu, click "Close and Return to Microsoft Word."
	
	To Rename a Macro
	-----------------
	
	1. Make sure the template or document containing the macro to rename is
	  currently open.
	
	2. On the Tools menu, point to Macro, and then click Macros.
	
	3. In the Macros In list, select the template or document containing the macro
	  you want to rename.
	
	4. In the list of available macros, select the macro to rename.
	
	5. Click Edit.
	
	6. In the Visual Basic Editor window, select the name of the macro that follows
	  the Sub statement.
	
	  For example, if your macro name is "MyMacro," you will see "Sub MyMacro()."
	  Select only the word "MyMacro" omitting "Sub" and the parentheses.
	
	7. Type a new name for the macro.
	
	8. On the File menu, click Save "<Project name>."
	
	9. On the File menu, click "Close and Return to Microsoft Word."
	
	To Delete a Macro
	-----------------
	
	1. On the Tools menu, point to Macro, and then click Macros.
	
	2. In the Macros dialog box, select the macro you want to delete in the list of
	  available macros.
	
	3. Click Delete.
	
	4. Click "Yes" when prompted to delete the selected macro.
	
	REFERENCES
	==========
	
	For more information about getting help with Visual Basic for Applications,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q163435 VBA: Programming Resources for Visual Basic for Applications
	
	Additional query words: wordcon kbmacro vba
	
	======================================================================
	Keywords          : kbProgramming kbualink97 word8 kbwordvba word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
