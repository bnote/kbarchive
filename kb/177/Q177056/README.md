---
layout: page
title: "Q177056: PRB: Return Parameter Variable Name for SQL Server Causes Error"
permalink: /kb/177/Q177056/
---

## Q177056: PRB: Return Parameter Variable Name for SQL Server Causes Error

{% raw %}

	Article: Q177056
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:2.5,2.6,5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbODBC kbSQLServ kbvfp kbvfp500 kbvfp500a kbvfp600 kbGrpDSFox kbGrpDSMDAC kbDSupport kb
	Last Modified: 21-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a, 6.0 
	- Microsoft Data Access Components versions 2.5, 2.6 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you call a Microsoft SQL Server Stored Procedure through ODBC and supply a
	variable for the return or OUTPUT parameter, a single character variable name
	causes an error.
	
	RESOLUTION
	==========
	
	Use a variable name with more than one character.
	
	In the example below, change the Callsp.prg variable name Z to more than one
	character, for example, Z1.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	With SQL ODBC driver version 3.50.0300 or later, the following error message is
	generated:
	
	  [Microsoft][ODBC SQL Server Driver]Invalid character value for cast
	  specification.
	
	With SQL ODBC driver version 2.65.0240, the following error message is
	generated:
	
	  [Microsoft][ODBC SQL Server Driver]Error in assignment.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Copy the following code into a file called Setup.prg:
	
	  
	
	        ********Start of Setup.prg***********
	        MyConnStr="'driver=sql server;server=myserver;uid=sa;pwd=mypass; "+ ;
	           "database=Pubs'"
	        *String to create the SQL Server Stored Procedure in Pubs
	        SP_String="Create Proc KBtemp @Param1 char(20)OUTPUT " + ;
	            "as Select @Param1='Return Success'"
	        CREATE DATABASE SP_Test
	        CREATE CONNECTION SP_Test CONNSTRING &MyConnStr
	        MyConn=SQLCONNECT('SP_Test')
	        IF MyConn > 0 then
	            rSucc1=SQLEXEC(MyConn, SP_String)
	            IF rSucc1 == -1 then
	                MESSAGEBOX("Creating Stored Procedure Failed")
	                AERROR(MyError)
	                ?"Create Stored Proc Error: "
	                DISPLAY MEMORY LIKE MyError
	            ENDIF
	            SQLDISCONNECT(MyConn)
	        ELSE
	            MESSAGEBOX("SQL Connection Failed")
	        ENDIF
	        *******End of Setup.prg*************
	
	NOTE: Replace the server, uid and pwd in the MyConnStr with the appropriate
	servername, user id, and password on your system.
	
	2. Copy the following code to a file called Callsp.prg.
	
	  
	
	        *******Start of CallSP.prg************
	        *Variable for the return parameter
	        Z=SPACE(25)
	        SP_Call="{Call KBTemp (?@Z)}"
	        MyConn=SQLCONNECT('SP_Test')
	        IF MyConn > 0 then
	            rSucc1=SQLEXEC(MyConn,SP_Call)
	            IF rSucc1<>-1 then
	                MESSAGEBOX(Z1)
	            ELSE
	                MESSAGEBOX("Calling Stored Procedure Failed")
	                AERROR(MyError)
	                ?"Calling Stored Proc Error: "
	                DISPLAY MEMORY LIKE MyError
	            ENDIF
	            SQLDISCONNECT(MyConn)
	        ELSE
	            MESSAGEBOX("SQL Connection Failed")
	        ENDIF
	        ******End of CallSP.prg*************
	
	3. Run Setup.prg.
	
	4. Run Callsp.prg.
	
	NOTE: Check the name of the stored procedure, KBTemp, with your Database
	Administrator to ensure it is correct to use.
	
	Additional query words: variable SQl odbc
	
	======================================================================
	Keywords          : kbODBC kbSQLServ kbvfp kbvfp500 kbvfp500a kbvfp600 kbGrpDSFox kbGrpDSMDAC kbDSupport kbMDAC250 kbMDAC260 
	Technology        : kbVFPsearch kbAudDeveloper kbMDACSearch kbMDAC250 kbMDAC260 kbVFP500 kbVFP600 kbVFP500a
	Version           : WINDOWS:2.5,2.6,5.0,5.0a,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
