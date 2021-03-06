---
layout: page
title: "Q199315: FIX: Method with BOOL&#42; Parameter Type Overwriting Memory in VB"
permalink: /kb/199/Q199315/
---

## Q199315: FIX: Method with BOOL&#42; Parameter Type Overwriting Memory in VB

{% raw %}

	Article: Q199315
	Product(s): Microsoft C Compiler
	Version(s): 5.0,6.0
	Operating System(s): 
	Keyword(s): kbAutomation kbCOMt kbMFC kbVBp kbVC500bug kbVC600bug kbGrpDSMFCATL kbNoUpdate
	Last Modified: 11-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Calling a Microsoft Foundation Class (MFC) COM Automation Object method with a
	Boolean* parameter type destroys the content of a variable in Visual Basic. For
	instance, see the following code:
	
	     void MyTest::Boo(BOOL FAR* p1);
	
	Where MyTest is an automation object in a MFC DLL (created with Class Wizard; a
	CCmdTarget-derived class with Creatable by Type ID option), and Boo is a method
	that has BOOL* as parameter type. Calling Boo in a Visual Basic application
	overwrites memory in Visual Basic.
	
	CAUSE
	=====
	
	The MFC AppWizard-generated automation object uses the data type BOOL* for the
	parameter. The BOOL type is four bytes in length. However, the Boolean variable
	in Visual Basic is only 2 bytes. As a result, the Automation method is writing
	into memory space occupied by another variable in Visual Basic.
	
	RESOLUTION
	==========
	
	Use VARIANT_BOOL* data type instead. VARIANT_BOOL is defined in OLE and is
	language-independent. VARIANT_BOOL is 2 bytes in length. However, the MFC Class
	Wizard does not show VARIANT_BOOL* in its drop-down list box as a choice for the
	parameter type. A workaround is to select BOOL* as the parameter's type as
	usual. Then manually change BOOL FAR* to VARIANT_BOOL FAR* in three files where
	this parameter is declared: .h/.cpp for automation object class and .odl file of
	the project. In addition, move the function prototype of the method out of the
	Class Wizard comments blocks because Class Wizard doesn't recognize the
	VARIANT_BOOL type. For example see the following code sample: In the .h file of
	MyTest class:
	
	     class MyTest : public CCmdTarget
	     {   
	         // ... other stuff
	
	         // Generated OLE dispatch map functions
	         //{{AFX_DISPATCH(MyTest)
	         // ... other stuff
	         //}}AFX_DISPATCH
	         afx_msg void Boo(VARIANT_BOOL FAR* p1);// USE VARIANT_BOOL and 
	                                                // MOVE OUT OF AFX_DISPATCH BLOCK!
	     };
	
	In the .cpp file of MyTest class:
	
	     void MyTest::Boo(VARIANT_BOOL FAR* p1) // USE VARIANT_BOOL!
	     {
	        // TODO: Add your dispatch handler code here.
	     }
	
	In the project's .odl file:
	
	     // ... other stuff
	     dispinterface IMyTest
	     {
	         // ... other stuff
	
	         methods:
	            // NOTE: ClassWizard maintains method information here.
	            //    Use extreme caution when editing this section.
	            //{{AFX_ODL_METHOD(MyTest)
	            // ... other stuff
	            //}}AFX_ODL_METHOD
	        [id(1)] void Boo(VARIANT_BOOL* p1);// USE VARIANT_BOOL and MOVE THIS
	                                           // OUT OF AFX_ODL_METHOD BLOCK!
	     };
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	This problem was corrected in Microsoft Visual C++ .NET.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new MFC AppWizard DLL project with all the default settings and
	  Automation support. Name the project AutoObj.
	
	2. Use Class Wizard to create a new CCmdTarget-derived class with Createable by
	  Type ID option selected. Name this class MyTest.
	
	3. Use Class Wizard to add a method to the IMyTest interface with a parameter
	  whose type is Bool*. Name the method Boo.
	
	4. Implement the method as shown below:
	
	     void MyTest::Boo(BOOL FAR* p1)
	     {
	        // TODO: Add your dispatch handler code here
	        *p1 = TRUE;
	     }
	
	5. Compile it and register AutoObj.dll.
	
	6. Start Visual Basic then Create a Standard EXE project and add a command
	  button to the form and use the following code to test the Automation object
	  you created above:
	
	     Private Sub Command1_Click()
	        Dim a As Integer
	        Dim b As Boolean
	        a = 123
	        b = False
	        Set test = CreateObject("AutoObj.MyTest")
	        test.Boo b
	        Debug.Print a, b    '<--- a is 0 - MEMORY IS TRASHED!
	     End Sub
	
	Notice that the value of variable "a" is changed to "0" after the Boo method on
	the test object has been called. Print output can be seen in immediate window.
	
	Additional query words: kbDSupport
	
	======================================================================
	Keywords          : kbAutomation kbCOMt kbMFC kbVBp kbVC500bug kbVC600bug kbGrpDSMFCATL kbNoUpdate 
	Technology        : kbAudDeveloper kbMFC
	Version           : :5.0,6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
