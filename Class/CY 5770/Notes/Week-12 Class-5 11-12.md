Start and Last

![[L13 Return-oriented Programming.pdf#page=45&selection=8,31,11,41]]![[L13 Return-oriented Programming.pdf#page=45&selection=4,11,4,16]]
Parameter is 4 byte
	+4 bytes is the return address

![[L13 Return-oriented Programming.pdf#page=45&selection=14,6,14,22]]
Stack is not executable

Only way
	ROP
		Control the Return Address
		![[L13 Return-oriented Programming.pdf#page=46&selection=0,14,2,1]]![[L13 Return-oriented Programming.pdf#page=46&selection=0,14,2,1]]![[L13 Return-oriented Programming.pdf#page=46&selection=4,0,4,15]]EAX->ESP
			Stack pointer to EAX
			Create another stack 

![[L13 Return-oriented Programming.pdf#page=48&selection=2,0,4,28]]
Last = Call (Indirect/Direct), Jump

Canary 찾는법
	Child= 같은 canary value (Fork)
		Parent - Child
			둘다 ASLR/카나리가 같음

Remotley
	Socket open = Not crash
	Socket close = Child process is crash (RESET)
Stack Reading Approach
	1. 매 바이트마다 덮어쓰기
	2. 콜백 함수 이건 
	3. 라이브러리 함수 인지 모른다


Valide gadget찾아도 알수 있는방법이 없다
Stop gadget = Triiger crash를 바로 하지 않는다
	pop rdi : segmentation fault
	sleep function and return -> remotley
1. Find a write operation (File descriptor, buffer, size, other parameters)
	1. POP rdi(NOT BE 0) -> rsi; and size (rsx)
	2. BROP Blind Rop Gadget


1. Control Flow Intergrity
	1. Shadow Stack
		1. Backward만 커버한다
		2. 2 Stackes (Original, Difdferent )
			1. 리턴주소만 모아서 stack을 만든다
			2. 리턴할때 비교해서 
				1. Backward 
		3. Fundting0> Function (Foward)
	3. Foward edg3e
		1. Call
	4. Backward Edge
		1. Return

실행되기전에 Control Graph 를 만들고 실횅하ㅓㄴ다
Code section이 not writable하면 된다

Direct Call
	Call 0x00000000 (Never been change)

Indirect Call
	Call RAX (subverted - attacker can change the value)
		Funtion pointer ()

Shadow
	RET to another stack![[L13 Return-oriented Programming.pdf#page=58&selection=0,25,0,38]]![[L13 Return-oriented Programming.pdf#page=58&selection=0,25,0,27]]
INT 80![[L13 Return-oriented Programming.pdf#page=54&selection=6,34,26,63]]