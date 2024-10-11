
# Clock
## Monotonicity Clock
시간은 앞으로만 가고 뒤로 안감
빠르면 시계를 느리게 돌림


Increase 
## Crisitan's algorithm
1. 클라이언트가 서버에 시간 보냄 (T1)
2. 서버가 클라이언트에 시간 보냄 (T2)
3. 클라이언트가 서버에게 시간 받음 (T3)

# Lamport Clock
1. 각 프로세스는 개인 시계카운터가 있다$$C_i$$
2. if a -> b $$C_i(a) < C_i(b)$$
3. 각각 프로세스는 이벤트가 성공할때 마다 +1을 한다
4. 보낼떼는 나의 시계 카운터를 보내면
5. 받을때는$$MAX(보낸에 시계, 받는애 시계) + 1$$
# Failure models
1. Fail Stop : 정확하계 감지/ 안살아남
2. Ommision: 무시 / 부분메세지만 전달됨
3. Network Partitioning: 프로세스 일부가 작동안함
4. Byzantine: 비잔친 

# Consensus
# Why?
1. 메모리 쓰고
2. DB 커밋
3. 파일시스템
4. 방송 (Totally Ordered)
## Properties
1. Agreement 모든 노드는 같은 값으로 consensus
2. Validity 값을 정할라면 그 값을 띄운 프로세스가 있다

# 수식
## Consensus
## Synchronous System without Crash Failures
1 Round
### Synchronous System with Crash Failures
f+1 round

# Failure Detector
## 1. Accuracy
## 2. Completeness


# Asynchronous
There is no deterministic algorithm that solves consensus in asynchronous settings with failures.

## FLP
FLP 정리는 **비동기 시스템**(메시지가 언제 도착할지 알 수 없고, 컴퓨터가 멈출 수 있는 시스템)에서 **단 하나의 컴퓨터라도 멈출 가능성이 있다면**:
- 비동기 시스템은 메세지 도착을 모른다
- 나머지 컴퓨터가 무슨값을 제안했느지 모른다
- 고장이 없어도 메세지가 지연되면 합의 안됨
• **비동기 시스템**에서는 **메시지가 언제 도착할지 모른다**.
• **컴퓨터가 멈출 가능성**이 있다면, **항상 합의에 도달하는 것은 불가능**하다.
• 이 결과는 **분산 시스템에서 모든 컴퓨터가 하나의 값에 합의하는 것이 얼마나 어려운지**를 보여줍니다.

• **항상 합의에 도달할 수 없다**는 것을 증명한 결과입니다.

## FLP -> Probalistic Randomization


## Valency
### 0 Valent
어떠한 경우도 0으로 결론이 난다
### 1 Valent
어떠한 경우도 1으로 결론이 난다
### BiValent
아직 모른다


Fault Tolerant
# Election Algorithm
Correctness - 선거가 끝나면 1명이 뽑히고 모두가 그 사람이 누군지 알아야한다
	1. Safety - 비정상인 애들 빼고 **ID가 가장 높은 애**가 뽑힌다
	2. Liveness - 알고리즘이 끝나면 **리더 1명**을 뽑아야 한다

# 문제점
1. 각각 노드는 누가 리더인지 모르고
2. 누구나 리더가 될수있고
3. 문제
	1. 메세지가 사라질수도 있고
	2. 프로세스가 죽을수도 있고
	3. 프로세스가 살아날수도 있고 (ELECTION 다시 한다)
끝나면 한명이 cordinator로 뽑혀야 한다

선거에는 알고리즘이 2개 있다.RING , BULLY.
# Ring vs BULLY
## Ring
Ring 에는 Unique Number가 있다
1 프로세스에는 1 기계
그리고 누군지 다 알고 있다 근데 status는 모른다
Highest ID = Leader
### Algorithm
1. Leader died -> sends an ELECTION to next process (ID도 포함해서)
2. 
### How works?
1. 이번 리더가 죽으면
	1. 선거 메세지를 다음 애 한테 보낸다 (ID)
2. ELECTION 메세지를 받으면
	1. 내 이름을 추가하고 다음으로 넘긴다
3. 시작한사람한테 돌아오면
	1. LEADER 메세지를 보낸다
4. LEADER 메세지가 돌아오면
	1. 끝

# Bully
1. Sychronous
2. Each other's ID
3. Failure detector
	1. Message Transmission Time
	2. Processing Time

## Election Trigger
1. Codrinator 죽으면
2. Cordinator 살아나면

# 원리
높은 번호의 프로세스가 낮은 번호를 괴롭힌다 한개의 프로세스가 남을때 까지
1. Election 메세지를 높은 ID로만 보낸다
	1. OK 메세지가 있으면
		1. wait for the LEADER message, if not coming, start a new election algorithm
	2. OK 메세지가 없으면
		1. send LEADER to all lower processes (Leader Selected)
# 실패시
자동으로 next highest ID process가 LEADER 메세지를 보낸다

# 몇개?
1. Best Case
	1. Second highest identifiew detects failure, elects it self
2. Worst Case
	1. Lowest identifier detects failure


```
	RING
```



# Multicast
## Property
### 1. Intergrity
메세지를 한번만 보낸다
### 2. Validity
언젠가는 자기가 메세지를 보낸다
### 3.Agreement
언젠가는 자기가 메세지를 받는다


Total Order , Partial Order , Causual Order
```mermaid
graph TD;
    A[Total Ordering] --> B[Partial Ordering]
    B --> C[Causal Ordering]
    A --> C
    A : 모든 프로세스가 이벤트 순서를 동의함
    A : 일관되고 전역적인 뷰를 제공함
    B : 일부 이벤트는 순서가 없음
    B : 전역 순서가 필요하지 않음
    B : 관련된 이벤트만 순서가 정해짐
    C : 사건은 인과 관계에 따라 순서가 정해짐
    C : A가 B를 유발하면, A는 B보다 먼저 발생해야 함
```