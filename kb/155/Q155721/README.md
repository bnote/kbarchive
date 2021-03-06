---
layout: page
title: "Q155721: FIX: Access Violation in RFX_Date If CTime Not Initialized"
permalink: /kb/155/Q155721/
---

## Q155721: FIX: Access Violation in RFX_Date If CTime Not Initialized

{% raw %}

	Article: Q155721
	Product(s): Microsoft C Compiler
	Version(s): 4.2
	Operating System(s): 
	Keyword(s): kbcode kberrmsg kbVC420bug kbVC500fix
	Last Modified: 04-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), included with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 4.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An application may fail with an access violation while executing the RFX_Date()
	function. A message similar to the following appears:
	
	  Unhandled exception in My.exe (MFC42D.DLL):
	  0xC0000005: Access Violation.
	
	CAUSE
	=====
	
	The RFX_Date() function in MFC 4.2 now requires initialization of CTime objects.
	Versions of MFC earlier than 4.2 do not have this requirement. AppWizard and
	ClassWizard do not initialize the CTime member variables for you.
	
	Because CTime member variables are not initialized in the CRecordset constructor,
	an access violation can occur when RFX_Date() tries to use the uninitialized
	data.
	
	RESOLUTION
	==========
	
	Initialize the CTime member variables in the constructor of your CRecordset-
	derived class. The following is one way to initialize the CTime member
	variable:
	
	     m_myTime = CTime::GetCurrentTime();
	
	STATUS
	======
	
	This problem was corrected in the MFC AppWizard included with Microsoft Visual
	C++, version 5.0. CTime member variables are now assigned a value of zero by the
	AppWizard. If a CRecordset class is manually added to your project that contains
	an empty recordset you still need to initialize the CTime member variable as
	explained in the RESOLUTION section.
	
	MORE INFORMATION
	================
	
	Here is one common scenario where you may see an access violation:
	
	  Call CRecordset::AddNew() on an empty recordset, set the value of the Ctime
	  member variable, and then call CRecordset::Update().
	
	  The insert to the database works; however, an access violation may occur
	  before the call to Update() returns.
	
	The following steps show how the access violation occurs:
	
	1. After the insert to the database is complete, Update() attempts to reload the
	  data for the previous record using the CRecordset::LoadFields() function.
	
	2. LoadFields() calls CRecordset::DoFieldExchange(), which calls the RFX_Date()
	  function for the CTime field.
	
	3. The CFieldExchange::LoadField case within RFX_Date() calls CTime::GetYear():
	
	        void AFXAPI RFX_Date(CFieldExchange* pFX, LPCTSTR szName, CTime&
	                             value)
	        {
	            ...
	            switch (pFX->m_nOperation)
	            {
	                ....
	                case CFieldExchange::LoadField:
	                {
	                    ...
	                    pts->year = (SWORD)value.GetYear();
	                    ...
	                }
	            ...
	        }
	
	The definition for GetYear() in AFX.INL dereferences the pointer returned from
	GetLocalTm(NULL):
	
	     _AFX_INLINE int CTime::GetYear() const
	         { return (GetLocalTm(NULL)->tm_year) + 1900; }
	
	GetLocalTm() returns the value from localtime(), which is a NULL pointer if the
	CTime value is a negative number. Because CTime has not been initialized, it may
	have a negative value. When GetYear() attempts to dereference this NULL pointer,
	the access violation occurs in AFX.INL at line 265.
	
	Additional query words: crash gpf exception kbDatabase kbMFC kbVC420bug kbVC500fix kbDSupport KBDSD
	
	======================================================================
	Keywords          : kbcode kberrmsg kbVC420bug kbVC500fix 
	Technology        : kbAudDeveloper kbMFC
	Version           : 4.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
