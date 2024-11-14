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

