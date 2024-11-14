Heap Implementation is changing
Prolog
	Compiler EBP constant value
	
> [!PDF|] [[L14 Heap Exploitation.pdf#page=4&selection=3,0,7,11|L14 Heap Exploitation, p.4]]
> > pool of memory used for dynamic allocations
> 
Standard C library (Malloc)x
NO SYSTEM CALL : Malloc

MMAP
	Memory Map
	Kernel 한태 가서 해야 되는데 느리다
	커널이 필요하지 않을수도
	20 바이트/10 바이트를 못 쓴다
	MMAP

DL 말록
	80년대 나옴
	ptmalloc 이 리눅스에서 쓴다 DL malloc (여러 스레드를 쓰개 한다)
	아직도 바뀌고 있다
	인터페이스는 같다 (명령어)
	kmalloc> [!PDF|] [[L14 Heap Exploitation.pdf#page=8&selection=4,1,4,7|L14 Heap Exploitation, p.8]]
> calloc
> [!PDF|] [[L14 Heap Exploitation.pdf#page=8&selection=18,1,18,8|L14 Heap Exploitation, p.8]]
> realloc
> [!PDF|] [[L14 Heap Exploitation.pdf#page=8&selection=16,0,20,5|L14 Heap Exploitation, p.8]]
> void *realloc(void *ptr, size_t size)
FAIL: 앞뒤에 데이터가 있으면

![[L14 Heap Exploitation.pdf#page=10&selection=22,1,24,21]]

HEAP은 특정 메모리 주소에 직접 접속
	엄청 길다
ldpreload -> 다른 라이브러리로 바꾸기

![[L14 Heap Exploitation.pdf#page=12&selection=4,8,4,12]]
큰 메모리들 할때


sbrk(NULL) = Program Break (컨셉)
Data 세그먼트 끝
Heap, BSS, DATA, TEXT

sbreak (200) = 늘릴수 있다
에러 뜬다

strace 아무 프로그램

Low to High (Heap)
![[L14 Heap Exploitation.pdf#page=14&selection=0,13,0,26]]![[L14 Heap Exploitation.pdf#page=14&selection=0,12,0,15]]
tcache
2 states
	1. In-Use (Malloc address is being)
	2. It was malloced before but it is freed
		1. 재사용 가능하다
다른 말록 바이트
10바이트
20바이트

지금 청크 사이즈

만약에 청크가 사용중이면
Freed가 없다
여기에는 니 데이터가 있다

Malloc 청크의 메모리주소를 넣는다

더블링크\

Former field
Backward Fiedld


16바이트로 alighment를 사용한다

P bit
	Is Previous chunk in use?
M bit
	MMAP()으로 받았냐?
A bit
	Thread Arena에 사용했나?

![[L14 Heap Exploitation.pdf#page=17&selection=6,0,7,0]]
ptmalloc코드에 더불어서 Threat Local Chachingj j 

Tcache 디자인
믿 청크 부분이 없다


Cache는 헤드에 간다
테일이 아니고
빠르다