![[L13 Return-oriented Programming.pdf#page=3&selection=6,15,6,41]]
어떻게든지 하이재킹 한다

buffer overflow = overwrite -> CPU execute the code
Hijack the control flow
Global Variables/Local Variables
Don't hijack the control flow

Code Injectio attack
	Shell code supplied by hacker
	Machine code = instructions

Code reuse attack
Return to libc attack

address space 에 있어야됨

return to some place => NOT oversrite, re use

Turing complete 하게

Innocent flesh = Random bytes
Code sequence
	Gadgets
		Some bytes > Not limited by compiler