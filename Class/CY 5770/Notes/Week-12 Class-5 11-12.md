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
	4. 