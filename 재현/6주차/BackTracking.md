# BackTracking
- 백트래킹이란 조건을 만족하는 한 계속 검사해 나가다, 조건에 부합하지 않는 순간 탐색을 취소하고 이전 단계로 돌아온 뒤 탐색을 이어나가는 알고리즘
- DFS 기반의 알고리즘으로, 재귀 함수나 스택을 통해 구현할 수 있다.

## 재귀
### BASE CASE
- 계산 없이 바로 답을 구할 수 있는 경우
- 재귀 호출을 멈추고 함수가 종료되는 조건
- 적어도 **하나 이상의 BASE CASE 가 존재**해야한다.

### RECURSIVE CASE
- 재귀 호출이 일어나는 경우
- 문제를 작은 부분으로 쪼개기 위함
- 함수가 호출될수록 **부분 문제가 BASE CASE 에 수렴**해야 함

## 재귀 예시
```java
class PrintNumber {
    public void asc(int n) {
        if (n == 0) return; // BASE CASE
        
        asc(n - 1);         // RECURSIVE CASE
        System.out.printf("%d", n);
    }
}
```

## 백트래킹 탬플릿
```java
void back_tracking(int count) {
    if (현재 상태가 마지막까지 도달한 경우) {
        정답 카운팅;
        return;
    }
    
    for (가능한 모든 경우에 대해) {
        if (조건을 만족하는 경우) {
            상태값 저장;
            back_tracking(count + 1);
            상태값 원복;
        }
    }
}
```

## 흐름 설명
- 우선 재귀적으로 실행할 함수를 선언
- 해당 함수에는 조건을 검사하기 위한 매개변수와 현재 상태를 체크하기 위한 매개변수가 필요
- 현재 상태가 마지막까지 도달한 경우, 가능한 경우의 수를 발견한 것이므로 정답을 카운팅
- 그 외의 경우에는 가능한 모든 경우에 대해 반복문을 돌며 검사
- 조건을 만족하는 경우 재귀적으로 호출
- 이때 DFS처럼 함수 호출 이전에 상태값을 저장하고 호출 후 원복 시킴으로서 검사가 끝난 케이스에 영향을 주지 않도록 함
- 조건을 만족하는 경우가 없다면 현재 호출 스택 이후로 돌아가므로 해당 상태 이후에 대한 탐색 중단

## 백트랙킹과 DFS의 차이점
### 백트래킹
- 어떤 노드에서 출발하는 경로가 그 해결책으로 이어질 것 같지 않으면 더 이상 경로를 탐색하지 않음으로써 시도 횟수 감소
- **불필요한 경로의 조기 차단**
- N!가지의 경우의 수를 가진 문제에 대해 백트래킹에 가하면 일반적으로 경우의 수가 줄어들지만 최악의 경우는 처리 불가능
- 모든 후보를 검사하지 않음

### DFS
- **모든 경로를 추적**
- N! 가지의 경우의 수를 가진 문제에 대해 깊이 우선 탐색을 이용하면 처리 불가능
- 모든 후보를 검사


### 정리

# ✅ 백트래킹 항목 정리

| 항목         | 설명                                                                 |
|--------------|----------------------------------------------------------------------|
| 정의         | 가능한 모든 경우를 탐색하되, 조건에 맞지 않으면 가지를 치며 탐색을 줄임 |
| 사용 방식    | 재귀 + 조건 검사 + 백트래킹(되돌아가기)                              |
| 시간 복잡도  | 최악의 경우 O(경우의 수), 하지만 가지치기로 줄일 수 있음              |
| 장점         | 완전탐색보다 효율적, 문제 해 구조 파악에 유리                         |
| 단점         | 문제 크기 커지면 느려짐, 가지치기 구현 실패 시 성능 저하              |


