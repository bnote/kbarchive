---
layout: page
title: "Q35545: Example Incorrect for the write() Function"
permalink: /kb/035/Q35545/
---

## Q35545: Example Incorrect for the write() Function

{% raw %}

	Article: Q35545
	Product(s): See article
	Version(s): 5.00 5.10 | 5.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | docerr | mspl13_c
	Last Modified: 26-SEP-1988
	
	The example for the write() function on Page 641 of the "Microsoft C
	5.1 Optimizing Compiler Run-Time Library Reference" is incorrect; it
	causes OS/2 to generate a General Protection (GP) fault.
	
	This example fails in OS/2 because it attempts to write 60,000 bytes
	from a buffer of size 6,000 bytes. In effect, it is attempting to read
	beyond the buffer of size 6000, causing the GP fault. In DOS, this
	error may go undetected, but an extra 54,000 bytes of random garbage
	may be written to the file.
	
	To work around this problem, change the number of bytes to write from
	60,000 bytes to 6000 bytes.

{% endraw %}
