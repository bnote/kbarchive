---
layout: page
title: "Q140306: HOWTO: Change a Grid's RecordSource Property Programmatically"
permalink: /kb/140/Q140306/
---

## Q140306: HOWTO: Change a Grid's RecordSource Property Programmatically

{% raw %}

	Article: Q140306
	Product(s): Microsoft FoxPro
	Version(s): 
	Operating System(s): 
	Keyword(s): kbcode kbvfp300 kbvfp500 kbvfp600
	Last Modified: 13-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article shows by example how to change the RecordSource property of a grid
	programmatically. It also allows you to click the column heading to change the
	order of the table.
	
	MORE INFORMATION
	================
	
	The method that does most of the work is SetGrid. It allows the user to select a
	table from an Open File dialog box. It sets the RecordSource property of the
	grid and the column headings to the field names in the table. It removes the any
	extra columns if the tables differ in the number of the fields they contain.
	
	The order is set in the Click event of the header. Setting the order by clicking
	the column header can only be done programmatically because it requires a
	subclass of the header. Columns and headers can only be subclassed in code.
	
	When the following code is run, the user will be presented with a dialog box to
	select a table. After table selection, the form appears. To change the table on
	which the grid is based, the user can click the button and they will again be
	presented with a dialog box to select a table.
	
	Sample Code
	-----------
	
	     * Begin Code
	     PUBLIC oGridForm
	     oGridForm = CREATEOBJECT("myForm")
	     oGridForm.Show
	
	     DEFINE CLASS myForm AS FORM
	
	         Height = 350
	         ADD OBJECT myGrid AS myGrid WITH Top = 20, LEFT = 20,;
	           Height = 200
	         ADD OBJECT myCommand as COMMANDBUTTON WITH Top = 250,;
	           Left = 20, Height = 30, Caption = "Change Grid"
	
	         PROCEDURE myCommand.Click
	             This.Parent.myGrid.SetGrid()
	             GO TOP
	             ThisForm.ReFresh
	         ENDPROC
	
	     ENDDEFINE
	
	     DEFINE CLASS myGrid AS GRID
	
	         ColumnCount = 0
	
	         PROCEDURE Init
	             This.Parent.myGrid.SetGrid()
	             ThisForm.Refresh
	         ENDPROC
	
	         PROCEDURE SetGrid
	             ThisForm.Lockscreen = .T.
	             lcFileName = GETFILE("DBF","Select the Table:")
	             USE (lcFileName)
	             lcAlias = ALIAS()
	             This.RecordSource = ""
	             This.RecordSource = lcAlias
	             SELECT (lcAlias )
	             FOR i = 1 TO FCOUNT()
	                 IF This.ColumnCount < i
	                    This.AddObject("column" + ALLTRIM(STR(i)),"MyColumn")
	                 ENDIF
	                 This.Columns(i).Visible = .t.
	                 This.Columns(i).ControlSource = FIELD(i)
	                 This.Columns(i).Header1.Caption = FIELD(i)
	             ENDFOR
	             FOR i = FCOUNT() + 1 TO This.ColumnCount
	                 This.RemoveObject("Column"+ALLTRIM(STR(i)))
	             ENDFOR
	             ThisForm.Caption = lcAlias
	             ThisForm.Lockscreen = .F.
	          ENDPROC
	
	     ENDDEFINE
	
	     DEFINE CLASS myColumn as Column
	
	         ADD OBJECT Header1 as myHeader WITH Visible = .T.
	
	     ENDDEFINE
	
	     DEFINE CLASS myHeader AS HEADER
	
	         PROCEDURE Click
	            FOR nCount = 1 TO 254
	                IF !EMPTY(TAG(nCount))
	                   IF This.Caption = TAG(nCount)
	                      SET ORDER TO This.Caption
	                      EXIT
	                   ENDIF
	                ELSE
	                   EXIT
	                ENDIF
	            ENDFOR
	            This.Parent.Parent.ReFresh
	            This.Parent.Parent.SetFocus
	         ENDPROC
	
	     ENDDEFINE
	     * End Code
	
	Additional query words:
	
	======================================================================
	Keywords          : kbcode kbvfp300 kbvfp500 kbvfp600 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP500 kbVFP600
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
