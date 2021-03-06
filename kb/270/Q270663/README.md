---
layout: page
title: "Q270663: HOWTO: Open a Secured Access Database from Visual C++"
permalink: /kb/270/Q270663/
---

## Q270663: HOWTO: Open a Secured Access Database from Visual C++

{% raw %}

	Article: Q270663
	Product(s): Microsoft C Compiler
	Version(s): winnt:6.0
	Operating System(s): 
	Keyword(s): kbDAOsearch kbJET kbMDAC kbMFC kbODBC kbVC600 kbGrpDSVCDB kbGrpDSMDAC kbDSupport
	Last Modified: 23-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to open a secured Microsoft Access database by using
	the Microsoft Foundation Classes (MFC) Data Access Objects (DAO) and Open
	Database Connectivity (ODBC) classes.
	
	MORE INFORMATION
	================
	
	Access databases may be secured by putting a password on the database itself, or
	by giving permissions to a specified user. When the security is applied at the
	user level, the application must be given the location of a workgroup
	information file. This file is named System.mdw by default, but you may give it
	a different name if you like. If you're using DAO, you must be sure to
	explicitly open a workspace using a valid user name and password before you open
	the database.
	
	Using Database Passwords with the MFC DAO Classes
	-------------------------------------------------
	
	With a database that has a database password, the password is stored in the
	database (.mdb) file itself, not in a separate file.
	
	The following code shows how to use MFC DAO to open a database that has a
	database password:
	
	  //myDB is a valid CDaoDatabase object.
	  myDB.Open("F:\\jet4.mdb",FALSE,FALSE,_T(";PWD=Test"));
	
	Using Database Passwords with the MFC ODBC Classes
	--------------------------------------------------
	
	The following example shows how to use MFC ODBC to open a database that has a
	database password. This code is from a CRecordset-derived class that was
	generated with the MFC AppWizard.
	
	  CString CSecuredRSSet::GetDefaultConnect()
	  {
	      return _T("ODBC;DSN=Secure;PWD=Lamont");
	  }
	
	Using User-Level Passwords with the MFC DAO Classes
	---------------------------------------------------
	
	The process is more complex if you are using the MFC DAO classes, and are
	connecting to a database that has user-level security. First, you need to set
	the SystemDB property of the DBEngine object to point to the appropriate
	workgroup information file. This must be done before any DAO objects have been
	initialized; otherwise, the setting has no effect. The code below is in the
	InitInstance function of a DAO MFC AppWizard application. Note that extra code
	is shown before and after the DAO code in order to illustrate where the DAO code
	would go in a typical InitInstance implementation:
	
	  // Parse command line for standard shell commands, DDE, file open.
	  CCommandLineInfo cmdInfo;
	  ParseCommandLine(cmdInfo);
	  /////////////////////////////////////////////////////////////////////////// 
	  // Inserted code does 2 things: Sets the version of DAO to use, and      // 
	  // sets the System.mdw file to the one that we want.                     // 
	  /////////////////////////////////////////////////////////////////////////// 
	
	  // Use DAO 3.6.
	  AfxGetModuleState()->m_dwVersion = 0x0601;
	
	  //Set the system DB to the one we want.
	  //May need to call AfxDaoTerm if DAO is already running
	  //	AfxDaoTerm(); 
	  CString strSystemMDB = "f:\\secured.mdw";
	  COleVariant varSystemDB( strSystemMDB, VT_BSTRT );
	
	  // Initialize DAO for MFC.
	  AfxDaoInit( );
	  DAODBEngine* pDBEngine = AfxDaoGetEngine( );
	  ASSERT( pDBEngine != NULL );
	
	  // Call put_SystemDB method to set the 
	  // system database for DAO engine.
	  DAO_CHECK( pDBEngine->put_SystemDB( varSystemDB.bstrVal ) );
	
	  /////////////////////////////////////////////////////////////////////////// 
	  /////////////////////////////////////////////////////////////////////////// 
	
	  // Dispatch commands specified on the command line.
	  if (!ProcessShellCommand(cmdInfo))
	       return FALSE;
	
	  // The one and only window has been initialized, so show and update it.
	  m_pMainWnd->ShowWindow(SW_SHOW);
	  m_pMainWnd->UpdateWindow();
	
	To open the database with the proper security, you first need to create a
	workspace with the required name and password, assign the workspace to the
	m_pWorkspace data member of the CDaoDatabase object, and then call Open. In the
	code below, myWS is a CDaoWorkspace that is defined in the CSecuredRSView class,
	and myDB is a CDaoDatabase, also defined in the view class. The code is the
	OnInitialUpdate method of the view class.
	
	  void CSecuredRSView::OnInitialUpdate()
	  {
	      m_pSet = &GetDocument()->m_securedRSSet;
	  	
	      // In order to open a secured Access DB we must have a Workspace
	      // that has been opened with the correct user name and password.
	      // Note that the system DB is not set here, because it was set in 
	      // InitInstance.
	      myWS.Create("New", "Lamont", "Lamont");
	      myWS.Append();
	
	      myDB.m_pWorkspace=&myWS;
	                myDB.Open("F:\\jet4.mdb",FALSE,FALSE,_T(";User=Lamont;PWD=Lamont;"));
	      m_pSet->m_pDatabase=&myDB;
	
	      CDaoRecordView::OnInitialUpdate();
	      GetParentFrame()->RecalcLayout();
	      ResizeParentToFit();
	  }
	
	Using User-Level Passwords with the MFC ODBC Classes
	----------------------------------------------------
	
	When connecting to the database through ODBC, it is much easier to specify which
	workgroup information file you want to use. Simply pass a parameter in the
	connection string that points to the workgroup information file to use. The code
	below is from a CRecordset-derived class that was generated with the MFC
	AppWizard.
	
	  CString CSecuredRSSet::GetDefaultConnect()
	  {
	      return           _T("ODBC;DSN=Secure;SystemDB=F:\\secured.mdw;User=Lamont;Pwd=Lamont");
	  }
	
	NOTE: In the case of user-level security, where you are specifying a workgroup
	information file, the version of the workgroup file must match the version of
	the database. Whether your database is in the Jet 3.51/Access 97 format or Jet
	4.0/Access 2000 format, the workgroup information file must also be in this
	format. The easiest way to ensure this is to include an appropriate workgroup
	information file in your application directory. Then open the database, passing
	the password as a parameter.
	
	REFERENCES
	==========
	
	MFC Technical Note 54 (TN054) in the MSDN Library
	
	Additional query words: system mdw uid cdatabase crecordset cdaorecordset user-level share-level
	
	======================================================================
	Keywords          : kbDAOsearch kbJET kbMDAC kbMFC kbODBC kbVC600 kbGrpDSVCDB kbGrpDSMDAC kbDSupport 
	Technology        : kbVCsearch kbAudDeveloper kbVC600 kbVC32bitSearch
	Version           : winnt:6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
