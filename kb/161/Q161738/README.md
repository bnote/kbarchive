---
layout: page
title: "Q161738: BUG: Large Memo Field Forces Undesired New Report Page"
permalink: /kb/161/Q161738/
---

## Q161738: BUG: Large Memo Field Forces Undesired New Report Page

{% raw %}

	Article: Q161738
	Product(s): Microsoft FoxPro
	Version(s): 3.0,3.0b,5.0,6.0
	Operating System(s): 
	Keyword(s): kbvfp kbvfp300BUG kbvfp500bug kbvfp600bug kbDSupport
	Last Modified: 16-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When a large memo field is included in a report where the detail band is wide
	(long from top to bottom), the Visual FoxPro Report Designer prints that memo
	field, then forces the remainder of the detail band to the next page, even
	though there is adequate space to print more detail on the current page.
	
	RESOLUTION
	==========
	
	If the report can be so designed, keep the detail band narrower, from top to
	bottom, than approximately four inches. This measurement in not exact as
	different reports work correctly at different band sizes. There are reports of
	bands six inches deep printing correctly.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a table using the following commands:
	
	        CREATE TABLE Test (first c(5),  firstmemo m, second c(5))
	        INSERT INTO Test (first, firstmemo, second) ;
	           VALUES ('abcde', REPLICATE("This is a wordy expression. ",30), ;
	           'zyxwv')
	
	2. Leave that table open in a workarea.
	
	3. Create a quick report based on the table you just created. To do this, click
	  New on the File menu and then select Report from the list of options. Click
	  the large New File command button at the top-right of the New dialog box.
	
	4. When the "Microsoft Visual FoxPro Report Designer" appears, click the Report
	  pad on the menu bar, then the Quick Report item from the pop-up menu.
	
	5. When the Quick Report dialog box appears, there are two large command buttons
	  in the area labeled "Field Layout." The right-hand button illustrates
	  vertical field alignment. Click it. Then click OK.
	
	6. The three fields of the table now appear in the "Detail" band of the report
	  being designed.
	
	  The format of the report is as follows:
	
	  a. The fields and labels are arranged vertically, the label for each field is
	     to the left of the field.
	
	     Below the detail band is the bar labeled "Detail." Move the cursor to that
	     bar. The cursor changes to a double-headed arrow. Click and drag the bar
	     down until the ruler at the left shows the detail band to be eight inches
	     in depth. This requires repeatedly scrolling down in order to see
	     drag-space at the bottom of the Report Designer's window.
	
	     An alternative to clicking and dragging the "Detail" band is to
	     double-click the Detail band to open up the Detail dialog box and change
	     the Height to 8 inches using the Spinner control.
	
	  b. All the fields and labels float, all the fields can stretch.
	
	     Those properties are set by default. To verify this one-by-one, position
	     the cursor over each field and label. Right-click to bring up the context
	     menu for that item. On the context menu click Properties. The Report
	     Expression dialog box appears. It shows the name of the field or label,
	     and that item's Field position. Be sure Float is the selected option. The
	     fields also show a check box labeled "Stretch with overflow." Be sure that
	     is checked. Labels do not have the "Stretch . . ." check box.
	
	  c. The memo field is narrow.
	
	     Click the memo field's text box to make it the "selected" control. It now
	     has handles (small black squares.) Click the center handle on the right
	     edge of the memo field, and drag that edge to the right to open the memo
	     field to nearly the full width of the page.
	
	7. Preview the report. (On the View menu, click Preview.)
	
	  You will see the following behavior:
	
	   - The label for the First field, and the field show where they would be
	     expected.
	
	   - The label for the Firstmemo field and the field show where they would be
	     expected.
	
	   - The label for the "Second" field is immediately beneath the label for the
	     "Firstmemo field.
	
	   - The rest of the page is blank.
	
	   - The field contents for the Second field is pushed to the next page.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbvfp kbvfp300BUG kbvfp500bug kbvfp600bug kbDSupport 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b kbVFP500 kbVFP600
	Version           : :3.0,3.0b,5.0,6.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
