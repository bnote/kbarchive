---
layout: page
title: "Q149320: BUG: First ListItem Truncated with ListView in Report View"
permalink: /kb/149/Q149320/
---

## Q149320: BUG: First ListItem Truncated with ListView in Report View

{% raw %}

	Article: Q149320
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 4.00 | 4.00
	Operating System(s): 
	Keyword(s): kbbuglist
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If the first item added to a ListView control set to Report view mode is added
	outside of the Form_Load event, the text of that item can be truncated and not
	displayed completely. Subsequent ListItem objects added to the ListView display
	their text correctly. The problem does not occur if the text of the ListItem
	object is specified with the Add method of the ListItem collection instead of as
	a separate property assignment.
	
	Another article detailing a somewhat similar problem with the ListView in Report,
	rather than List, view mode is article Q149264, "BUG: ListView in Report View
	Truncates First ListItem." This article outlines the different symptoms of that
	problem in addition to a different workaround.
	
	WORKAROUND
	==========
	
	This problem can be avoided in two ways:
	
	- Add the initial ListItem to the ListView during the Form_Load event rather
	  than adding at a later time.
	
	-or-
	
	- Specify the text of the initial ListItem in the Add method of the ListItem
	  collection object instead of as a separate property assignment. For example,
	  instead of using this code (assuming lv is a ListItem object)
	
	        Set lv = ListView1.ListItems.Add
	        lv.Text = "This is the string"
	
	  use:
	
	        Set lv = listview1.ListItems.Add(, , "This is the string")
	
	  Any strings added after the initial item can be added in any manner from any
	  where in code.
	
	STATUS
	======
	
	Microsoft has confirmed this to be an issue in the Microsoft products listed at
	the beginning of this article. Microsoft is researching this problem and will
	post new information here in the Microsoft Knowledge Base as it becomes
	available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce
	------------------
	
	1. Start Visual Basic 4.0. Form1 is created by default.
	
	2. Add a single ListView control to the form1.
	
	3. Add this code to the project:
	
	     Private Sub Form_Load()
	         ListView1.View = lvwReport
	         ListView1.ColumnHeaders.Add , , "Goo"
	     End Sub
	
	     Private Sub FOrm_Click()
	         Dim lv As ListItem
	
	         Set lv = listView1.ListItems.Add
	         lv.Text = "THIS IS A VERY LONG STRING"
	     End Sub
	
	4. Press F5 or select Start from the Run menu to run the application.
	
	5. Click the form once and see that the new entry to the ListView is truncated
	  and is not completely displayed. Any subsequent clicks to the form after this
	  will result in the correct string being displayed.
	
	Additional query words: 4.00 vb4win vb432
	
	======================================================================
	Keywords          :  kbbuglist
	Technology        : kbVBSearch kbAudDeveloper kbVB400Search kbVB400
	Version           : 4.00 | 4.00
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
