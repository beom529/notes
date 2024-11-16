# Research Direction
1. CFI on GPU / Create a Code
	1. ROP paper 참고해서 LLM의 1 layer 기준으로 CFI 문제 없는지 확인하기
	2. Architecture Research
	3. Coverage Based Fuzzing
	4. Firmware Fuzzoing
		2. BUT inturrupt hanlding
		3. PTE not on that part
2. GCC Instrument -> Coverage based
	1. Confidential Computing on GPU
	2. Limitation? : 현재방법이 가장 좋은 방법인지?
	3. Reverse Engineering? : 현재방법의 구멍은 없는지
	  
# **PAPER**

1. EVALUATION에 RESEARCH QUESTION 넣기
# **TO-DO LIST**

## **RESEARCH**

- [ ] AFL 사용할줄알기
	- [ ] Coverage based fuzzing에 대해서 공부하기
	- [ ] Coverage GCC? 컴파일러마다 다른가?
	- [ ] 소스코드 / 바이너리 없이 실행
- [ ] MIG 페이퍼 읽기
	- [https://dl.acm.org/doi/pdf/10.1145/3576915.3616672](https://dl.acm.org/doi/pdf/10.1145/3576915.3616672)
- [ ] 차오밍 Paper 읽기 (SHiFT: Semi-hosted Fuzz Testing for Embedded Applications)
	- [ ] https://www.usenix.org/conference/usenixsecurity24/presentation/mera
- [ ] Blackbox Paper 읽기 (Threat Model, Scenario 집중할것)
	- LABRADOR: Response Guided Directed Fuzzing for Black-box IoT Devices
		- [https://www.computer.org/csdl/proceedings-article/sp/2024/313000a127/1Ub23HQTJ1C](https://www.computer.org/csdl/proceedings-article/sp/2024/313000a127/1Ub23HQTJ1C)
	- Snipuzz: Black-box fuzzing of iot firmware via message snippet inference
		- [https://dl.acm.org/doi/10.1145/3460120.3484543](https://dl.acm.org/doi/10.1145/3460120.3484543)
	- U-Fuzz: Stateful Fuzzing of IoT Protocols on COTS Devices
		- [https://ieeexplore.ieee.org/document/10638624](https://ieeexplore.ieee.org/document/10638624)
	- Sok: Prudent evaluation practices for fuzzing
		- [https://oaklandsok.github.io/papers/schloegel2024.pdf](https://oaklandsok.github.io/papers/schloegel2024.pdf)
	- Side-channel aware fuzzing
		- [https://link.springer.com/content/pdf/10.1007/978-3-030-29959-0.pdf](https://link.springer.com/content/pdf/10.1007/978-3-030-29959-0.pdf)
	- Powertrace-based Fuzzing of CAN Connected Hardware
		- [https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=985029](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=985029)
- [ ] EM-FUZZING 사용하기
	- Probe 넣어서 사용
- [ ] GPU Schedule은 SAGAR가 한다
- [ ] LLM Layer Security (주 실행은 Python -> CUDA 코드로 변환됨)
	- [ ] LLAMA
	- [ ] GROK
- [ ] https://oaklandsok.github.io/papers/schloegel2024.pdf
- [x] Thanksgiving에 수업 있다

## **CLASS**
1. Solana 이해하기
	1. 거래 (A->B) 생기면 어떻게 되는지
		1. 
2. MEV 이해하기
	1. DeFI
	2. DEX
	3. 
3. Solana 페이퍼가 있나
	1. 