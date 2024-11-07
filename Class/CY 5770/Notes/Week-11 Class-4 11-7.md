Gadgets address base and reuse it

ADD REGISTER
1. PUt that value on the stack
2. POP gadget
SKIP REGISTER
1. POP gadget
NOP
1. ret;
	1. Go to next address and next gadget
	2. SKIP and go NEXT
2. nop ret
STACK PIVOTING
1. xchg
	1. EXCHANGE REGISTER VALUE
	2. ATOMIC instruction
	3. exchange RSP
	4. Original space
	5. NO limitation of overflowed stack anymore
2. LOC

syscall instuction
	VERY RARE

OPEN FILE/READ FILE/CHANGE THE OWNER/CHANGE OF THE PERMISSION
> Function call to C library (Systemcall wrapper) -> 

OPEN THE FLAG and print value