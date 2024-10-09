
# Clock
## Monotonicity
시간은 앞으로만 가고 뒤로 안감
빠르면 시계를 느리게 돌림

## Crisitan's algorithm
1. 클라이언트가 서버에 시간 보냄 (T1)
2. 서버가 클라이언트에 시간 보냄 (T2)
3. 클라이언트가 서버에게 시간 받음 (T3)

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

