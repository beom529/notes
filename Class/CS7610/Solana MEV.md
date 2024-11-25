- 기존 금융소는 CEX 모델 사용
	- 팔고 진짜 돈으로 바꾸고 다른 코인 삼
- DeFI는 DEX로 두 코인을 직결해서 거래함
	- Swap

# Smart contract
	개인간 거래
	금융기관이 관여 안함
	별도의 중개자 없이 1:1 로 바로 거래
		A (1) : B(2)
	사실상 Colletrol 대출
		물물교환
	
	

# Mempool, Staking
## 스테이킹
## 멤풀
거래발생 -> 멤풀(임시)에 잠깐 보관 -> Miner가 채굴하면 그때 거래가 완성

# POW (작업증명)

# POS (지분증명)
# MEV
- Maximal Extractable Value (최대 추출 가능 가치)
### POW
- 채굴자가 불록 생성
### POS


Uniswab


# SOLANA
1. MEV 탐지
	1. 샌드위치 공격을 막기 위해서는 
2. 


Var synchrony model 


# PBFT가 문제가 안되는 이유?
Byzantine이 문제가 안되는 이유

Assumption
모두가 연결되어 있기 때문에
P2P에는 멀티홉연결이 된다

직접 소통하는 채널이 있으면 Veryfiyt 를 직접 할수 있다

Crip 

Disjoint Path
OVerlap이 안되는 Path가 있다
K , K-a ()
As long as less attackers in paths, it will work.



1. Raydium 1



History

Full Transaction


Deterministic
	Pattern
		Large Transaction (Same Amount)	-> 2 Transaction -> From amount 
		Could be 

DEX
	Comparing with that
	MEV Cross ethereum -> 1 Exchange
		Prices are Arbitrage will be between the exchanges
	MEV different block chain
	Most likley that's the case
	Arbitrage
	Same block -> 
	Pattern

1 Exchange
	1. DEX Large Transaction > Exchange Price를 바꿀만큼 큰 건만 할수 있다
	2. Arbitrage , Liquidation을 볼수 있을것이다 (Multiple Blocks, Same Transaction)
	3. Assets that are
	4. All the Trade on the exchange

Large Transasction
	Not the Magnitude
	How the change compare to the transaction fee going to be 
		Addresses and instructions
	Data 대신에 데이터 포인터를 사용한다

Solana program -> Instructions are different -> Account

Query -> Voting on chain 

Smaller space
	Mempool 없이
	Attack Surface? 

Intrin

APE Transaction
	Copy the transaction -> 

Mempool

Minimizing risk / transaction : Availability 


50ms 40ms

솔라나
	Bots -> Fail 되명 VALIDATOR는 돈을 받지 않는다

Validator가 돈을 번다


Not the Validator's Address 
1. Identify the validator

Slashing -> What is wrong -> Half of Eth
Certain Leaders are dping this

1 block -> 1 Leader

4 blocks per validator

7 days

MEV 검색하기


Addresses , Assets being trade, amount 

1DEX
4 Blocks


Epoch 1
 ├─ Slot 0 ── Leader A ── Block 0
 │                └─ Transaction 1: User A → User B
 │                └─ Transaction 2: User C → User D
 │
 ├─ Slot 1 ── Leader B ── Block 1
 │                └─ Transaction 3: 스마트 계약 실행
 │                └─ Transaction 4: User X → User Y
 │
 ├─ Slot 2 ── Leader C ── Block 2
 │                └─ Transaction 5: User Z → User W
 │
 └─ Slot 3 ── Leader D ── Block 3
                  └─ Transaction 6: User E → User F

최대한 간단하게 ¸¸
1. 왼쪽 위 : Current Epoch : {}
2. 다음 문단 : 사각형 Canvas에 다음과 같은 도형을 실시간으로 그려야되
	1. 제일 큰 사각형 은 Epoch 이고 왼쪽 위에 Epoch : {Epoch번호}가 떠야되
	2. 그다음 작은 사각형이 제일 큰 사각형 위에 있어. 각각 사각형은 Slot 이고 Slot 번호가 떠야되 각 슬롯 은 선이 이어져 있어 []-[]-[] 이런 느낌
	4. Slot 사각형 안에는 Block이 있고 Block 번호가 떠 마우스를 올리면 해당 Block에 대한 Metadata가 전부 오른쪽 단에 올라와
3. 방금 문단의 오른쪽에는 Block 메타데이터 또는 마우스가 올라간 곳의 Metadata가 올라 와야되
4. 아래 문단에는 마우스가 클릭한 블록의 Transaction이 차례대로 쭉 나와 (표)
5. 방금 표 아래에는 "같은 Validator 묶기"버튼이 있어 이 버튼을 누르면 같은 Validator 가 만든 Block이 위 캔버스에 하이라이트 되고 아래 표에는 4개 Block의 Transaction 표가 Concat 되서 올라와
데이터의 소스는 Solana public API HTTP,WS 전부 다 써야되 실시간으로 데이터를 불러 와야되.

왼쪽 윗 문단
현재 Epoch
현재 Block

왼쪽 중간문단
파일트리 형식으로 믿에 처럼 실시간으로 리스트를 만들어줘
Epoch 1
 ├─ Slot 0 ── Leader A ── Block 0
 ├─ Slot 1 ── Leader B ── Block 1
 ├─ Slot 2 ── Leader C ── Block 2
 └─ Slot 3 ── Leader D ── Block 3

왼쪽 아랫문단
Transaction Detail Table (순서대로) 표시할수 있는건 전부 표시해줘

오른쪽 문단
클릭한 Block의 메타 데이터

전부 실시간으로 올라와야되

Electron을 이용해서 Solana 어플리케이션을 만들고 있어 굉장히 단순한 프로그램인데 다음과 같은 기능이 동작해야되.

1. Solana의 Websocket과 HTTP API를 이용해서 실시간으로 현재 Epoch,Slot,Block으로 불러와야되
2. 불러온 데이터는 다음과 같게 화면에 표시 되야되
	1. 왼쪽 윗 문단
		현재 Epoch
		현재 Block Number
		현재 Leader
	2. 왼쪽 중간문단
		트리 형식으로 믿에 처럼 실시간으로 리스트를 만들어줘
		Epoch 1
		 ├─ Slot 0 ── Leader A ── Block 0
		 ├─ Slot 1 ── Leader B ── Block 1
		 ├─ Slot 2 ── Leader C ── Block 2
		 └─ Slot 3 ── Leader D ── Block 3
		실시간으로 블록이 추가 될때마다 자동으로 아래에 추가 되야되
	1. 왼쪽 아랫문단
		Transaction Detail Table (순서대로) 표시할수 있는건 전부 표시해줘 클릭한 Block의 데이터만 표시 하면되
		Table 이 Dynamic 했으면 좋겠어 따른 라이브러리를 써도 되
	4. 오른쪽 문단
		클릭한 Block의 메타 데이터를 표시 해야되
3. 추가적으로 Solana에서는 1 Validator가 4개의 Slot을 할당 받잖아 그래서 맨 밑에 버튼을 누르면 한 Validator가 만든 연속적인 블락의 모든 Transaction이 전부 append 되서 나와야되 그리고 위의 다이어그램에서도 Highlight 되야되.
4. MEV 필터링 버튼이 있고 누르면 다음 Transaction이 하이라이트 되야되
	1. A 가 B로 Transaction을 함 (amount : X)
	2. 큰 Transaction이 있음
	3. B 가 A로 Transaction (amount : X)
5. 가능하면 코드를 별도의 파일에 분리하지 말고 한번에 작성해줘.


Bitquery API 를 이용해서 Solana의 MEV를 탐지 할려고 해. 현재 계획은 Sandwichi, Back-running, Front-running을 탐지할려고 하고, graphQL을 사용하고 싶어 코드를 만들어줘. 컨셉은 Solana는 1 Node가 4개의 연속된 Slot을 받잖아. 이 4개의 Slot의 Transaction을 Concat 해서 MEV Transaction을 찾고 싶어, 파이선 코드를 만들어줘.