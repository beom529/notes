
# Clock
## Monotonicity Clock
시간은 앞으로만 가고 뒤로 안감
빠르면 시계를 느리게 돌림

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