---
layout: page
title: "Q154825: HOWTO: Extract Multiple RDO Resultsets from Stored Procedures"
permalink: /kb/154/Q154825/
---

## Q154825: HOWTO: Extract Multiple RDO Resultsets from Stored Procedures

{% raw %}

	Article: Q154825
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbRDO kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVBDB kbDSupport
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	SQL Server stored procedures are capable of returning more than one recordset
	and the Remote Data Object (RDO) has the ability to access these Multiple
	Resultsets.
	
	When calling these stored procedures, the following error can be encountered:
	
	  Error 40002
	
	  "37000: [Microsoft][ODBC SQL Server Driver][SQL Server]Cannot open a cursor on
	  a stored procedure that has anything other than a single
	  select statement in it"
	
	The following code sample showing how to return the multiple Resultsets using the
	MoreResults Property of the RDO.
	
	MORE INFORMATION
	================
	
	There are two methods to avoid Error 40002.
	
	Method 1
	--------
	
	Use The ODBC Cursor library rather than Server Side Cursors. To do this, use the
	following code:
	
	     rdoEngine. rdoDefaultCursorDriver = rdUseODBC
	
	  - or -
	
	     rdoEnvironments(0).CursorDriver = rdUseOdbc
	
	This option gives better performance for small result sets, but may degrade
	quickly for larger result sets depending on the Server and workstation
	configuration.
	
	NOTE: If you are using SQL text fields, you must use Server-side cursors to
	bypass Error 40002"
	
	Method 2
	--------
	
	Use Server Side Cursors, a Forward Only Cursor, and a rowset size of 1. Make the
	server create a cursor-less resultset on the server side by using a forward only
	cursor and a RowSetSize of 1.
	
	The following code sample illustrates how to create a stored procedure that
	returns multiple result sets using method 2.
	
	1. Create the stored procedure on SQL Server:
	
	  a. Start the ISQL utility that shipped with SQL server.
	
	  b. Connect to your SQL server.
	
	  c. Select the pubs database from the combo box labeled DB.
	
	  d. Enter the following lines into the Query Tab:
	
	        CREATE PROCEDURE TestMultiResults AS
	        select * from authors
	        select * from discounts
	        GO
	   
	
	  e. Choose the Query|Execute menu. The Results tab should display:
	
	     This command did not return data, and it did not return any rows
	
	     A stored procedure called TestMultiResults has now been created in the pubs
	     database on SQL Server.
	
	2. Create the Visual Basic client to call the stored procedure:
	
	  a. Start Visual Basic. Form1 is created by default.
	
	  b. Add a Command Button (Command1) and a List Box (List1) to Form1.
	
	  c. Add the following code to Form1:
	
	        Private Sub Form_Load()
	           Command1.Caption = "Run Stored Procedure"
	        End Sub
	
	         Private Sub Command1_Click()
	          Dim cn As rdoConnection
	          Dim ps As rdoPreparedStatement
	          Dim rs As rdoResultset
	          Dim strConnect As String
	          'set cursor driver to use server-side cursors
	          rdoDefaultCursorDriver = rdUseServer
	
	          'open a connection to the pubs database using DSNless connections
	          'replace myServer with the name of your SQL server
	
	          strConnect = "Driver={SQL Server}; Server=myServer; " & _
	                       "Database=pubs; Uid=sa; Pwd="
	          Set cn = rdoEnvironments(0).OpenConnection(dsName:="", _
	                                                Prompt:=rdDriverNoPrompt, _
	                                                ReadOnly:=False, _
	                                                Connect:=strConnect)
	
	          'create a prep stmt for the stored proc call
	          Set ps = cn.CreatePreparedStatement("MyPs", _
	                                              "{call TestMultiResults}")
	          'set the RowSet size to 1
	           ps.RowsetSize = 1
	
	           'open the resultset with forward-only cursor
	           Set rs = ps.OpenResultset(rdOpenForwardOnly)
	
	           'add the first resultset to a list box
	           While Not rs.EOF
	               list1.AddItem rs("au_fname") & " " & rs("au_lname")
	               rs.MoveNext
	           Wend
	
	           'move to the second resultset
	           rs.MoreResults
	           list1.AddItem "Second Resultset Below"
	           'add the second resultset to the same list box
	           While Not rs.EOF
	               list1.AddItem rs("discounttype") & " = " & rs("discount")
	               rs.MoveNext
	           Wend
	
	           'Close the resultset and the connection and set both to nothing
	           rs.Close
	           Set rs = Nothing
	           cn.Close
	           Set cn = Nothing
	        End Sub
	   
	
	  d. Run the project and click the "Run Stored Procedure" button. You should
	     see a list of Authors and then Discounts in the list box.
	
	REFERENCES
	==========
	
	For more information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q147875 HOWTO: Use "DSN-Less" ODBC Connections with RDO and DAO
	
	  Q147814 HOWTO: Retrieve Multiple Result Sets from a Stored Procedure
	
	  Q149054 INFO: Choosing a rdoResultset Cursortype
	
	Additional query words: kbVBp400 kbVBp500 kbVBp600 kbdse kbDSupport kbRDO kbVBp
	
	======================================================================
	Keywords          : kbRDO kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVBDB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400
	Version           : WINDOWS:4.0,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
