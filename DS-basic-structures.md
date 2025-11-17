# DS-005
배열(Array) & 리스트(List) 핵심
## 배열

연속된 메모리

인덱스 접근 O(1)

삽입/삭제 O(n)

## 연결 리스트

메모리 비연속

노드 = (값, next 포인터)

중간 삽입/삭제 O(1)

인덱스 접근 O(n)

# DS-006
스택(Stack) & 큐(Queue)
## 스택

LIFO

push/pop → O(1)

사용 예: 함수 호출, 되돌리기

## 큐

FIFO

enqueue/dequeue → O(1)

사용 예: 은행 대기열, BFS

# DS-007
트리(Tree) & 힙(Heap)
## 트리

계층 구조

이진 탐색 트리(BST)는

탐색 O(log n)

삽입/삭제 O(log n)

## 힙

최소/최대 우선순위 보장

삽입 O(log n)

top 조회 O(1)

구현: 배열 기반 완전 이진트리

# DS-008
해시(Hash) / HashTable
## 개념

key → hash() → index

평균 O(1)

충돌 처리 필요

## 충돌 처리

chaining(연결리스트)

open addressing(선형 탐사, 이중 해싱)

# DS-009
정렬(Sort)
## 느린 정렬

버블, 선택, 삽입 → O(n²)

## 빠른 정렬

퀵 정렬: 평균 O(n log n)

병합 정렬: O(n log n) 안정적

힙 정렬: O(n log n)

# DS-010
탐색(Search)
## 선형 탐색

순서대로 탐색

O(n)

## 이진 탐색

정렬된 배열에서만 가능

O(log n)

# DS-011
Big-O 시간복잡도
## 순서

O(1)

O(log n)

O(n)

O(n log n)

O(n²)

## 팁

상수는 버린다

높은 차수를 가진 항만 본다

계산량의 증가 속도를 나타낸 것
