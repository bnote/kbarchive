---
layout: page
title: "Q73850: PRB: Variables with Local Scope to Switch Won't Be Initialized"
permalink: /kb/073/Q73850/
---

## Q73850: PRB: Variables with Local Scope to Switch Won't Be Initialized

{% raw %}

	Article: Q73850
	Product(s): Microsoft C Compiler
	Version(s): 1.0,1.5,2.0,2.1,4.0,5.0
	Operating System(s): 
	Keyword(s): kbLangC kbVC100 kbVC150 kbVC200 kbVC210 kbVC400 kbVC500
	Last Modified: 12-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, versions 1.0, 1.5, 2.0, 2.1, 4.0 
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	- Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In Microsoft C, variables may be declared as local to a switch statement by
	defining them within the braces that make up the switch. They then have
	visibility and life for the duration of the switch statement. However, because
	of the design of a switch block, they will not be initialized when declared
	unless the variable is static or is declared after a case label.
	
	RESOLUTION
	==========
	
	If you must declare an initialized variable that is local to the switch
	statement and transient in duration, use brackets before and after the switch
	and place the declaration outside the switch statement.
	
	MORE INFORMATION
	================
	
	The ANSI Standard (Section 3.6.4.2) states:
	
	  A "switch" statement causes control to jump to, into, or past the statement
	  that is the switch body, depending on the value of a controlling expression,
	  and on the presence of a "default" label and the values of any "case" labels
	  on or in the switch body. A "case" or "default" label is accessible only
	  within the closest enclosing "switch" statement.
	
	  The integral promotions are performed on the controlling expression. The
	  constant expression in each "case" label is converted to the promoted type of
	  the controlling expression. If a converted value matches that of the promoted
	  controlling expression, control jumps to the statement following the matched
	  "case" label. Otherwise, if there is a "default" label, control jumps to the
	  labeled statement. If no converted case constant expression matches and there
	  is no default label, no part of the switch body is executed.
	
	Compiling the sample code below and runnning the resultant executable
	demonstrates this problem. The following text will be output:
	
	  local_int NOT initialized
	
	There are three options available to ensure that the variable local_int is
	initialized to the correct value (5 in this case):
	
	- Declare it outside the switch statement, using braces to limit its scope if
	  necessary. For example:
	
	  {
	     int local_int = 5;
	     switch (param)
	     {
	        case 100:
	           local_int+=5;
	           rc = (local_int == 10 ? 1 : 0);
	           break;
	        default:
	           break;
	     }
	  }
	
	- Declare after each case label in which it is to be used. For example:
	
	  switch (param)
	  {
	     case 100:
	     {
	        int local_int = 10;
	        rc = (local_int == 10 ? 1 : 0);
	        break;
	     }
	     case 101:
	     {
	        int local_int = 11;
	        rc = (local_int == 10 ? 1 : 0);
	        break;
	     }
	     default:
	        break;
	  }
	
	- Declare the variable as static.
	
	  /* Compile options needed: none
	  */ 
	
	  int _cdecl printf(const char *, ...);
	  int switch_func(int);
	  int main(void);
	
	  int main(void)
	  {
	     int rc = switch_func(100);
	
	     if ( rc )
	        printf("local_int initialized\n");
	     else
	        printf("local_int NOT initialized\n");
	
	     return( rc );
	  }
	
	  int switch_func(int param)
	  {
	     int rc = 0;
	
	     switch (param)
	     {
	        int local_int = 5;
	        case 100:
	           local_int+=5;
	           rc = (local_int == 10 ? 1 : 0);
	           break;
	        default:
	           break;
	     }
	
	     return( rc );
	  }
	
	Additional query words:
	
	======================================================================
	Keywords          : kbLangC kbVC100 kbVC150 kbVC200 kbVC210 kbVC400 kbVC500 
	Technology        : kbVCsearch kbVC400 kbAudDeveloper kbvc150 kbvc100 kbVC500 kbVC200 kbVC210 kbVC32bitSearch kbVC500Search
	Version           : :1.0,1.5,2.0,2.1,4.0,5.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
