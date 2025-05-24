
---

### 1. 시간복잡도와 공간복잡도

* **Big-O / Big-Theta / Big-Omega**:

  * **Big-O**: 최악의 경우 (상한)
  * **Big-Θ**: 평균적인 경우 (정확한 경계)
  * **Big-Ω**: 최선의 경우 (하한)
* **왜 Big-O?**: 안전하게 최악의 경우 성능 보장 (면접과 실무에서 중요)
* **O(1)이 무조건 빠를까?**: "무조건은 아님". 상수 시간이 실제로 오래 걸릴 수도 있음.

---

### 2. 링크드 리스트

* **배열 vs 링크드 리스트**:

  * 배열은 인덱스로 접근 O(1), 삽입/삭제 O(N)
  * 링크드는 접근 O(N), 삽입/삭제 O(1)
* **응용 자료구조**:

  * 스택, 큐, 해시 테이블(Chaining), 이중 연결리스트 등

---

### 3. 스택과 큐

* **스택 2개로 큐**:

  * 하나는 입력용, 하나는 출력용
  * 전체 시간복잡도는 amortized O(1)
* **큐 2개로 스택**:

  * 입력 시는 그대로, 출력 시 재배열 → O(N)
* **Infix/Prefix/Postfix**:

  * Postfix는 스택으로 계산 용이 (연산자 만나면 피연산자 2개 pop → 계산)
* **Deque 구현**:

  * 이중 연결 리스트 or 원형 배열
* **C++에서 O(1) Random Access**:

  * Deque는 여러 고정 크기 버퍼로 구성되어 있으며, 버퍼 배열의 인덱스를 사용

---

### 4. 해시 자료구조

* **좋은 해시 함수**:

  * 충돌 최소화, 균등 분포, 단순 연산
* **충돌 해결**:

  * 체이닝, 오픈 어드레싱, 이중 해싱
* **Double Hashing**:

  * 장점: 클러스터링 방지
  * 단점: 2차 함수 필요, 삭제 어려움
* **Load Factor**:

  * 요소 수 / 테이블 크기. 보통 0.75 이상이면 resize
* **멀티스레드 환경 대응**:

  * Lock striping, ConcurrentHashMap 사용 등

---

### 5. 트리와 이진탐색트리

* **그래프 vs 트리**:

  * 트리는 사이클 없는 방향 비순환 그래프 (DAG)
* **중위순회**: 오름차순 정렬 결과
* **삽입/삭제**: log N (균형 유지된 경우), 최악 O(N)
* **한계점**: 편향 트리 → 성능 저하
* **삼진탐색트리**: 개념 가능, 성능/복잡도 면에서 실용성 낮음

---

### 6. 힙

* **배열 구현**:

  * 부모(i): i, 왼쪽 2i+1, 오른쪽 2i+2
* **삽입/삭제**:

  * Heapify 과정을 통해 log N 유지
* **편향 없음**:

  * 배열 기반으로 완전 이진 트리 구조 유지
* **Heap Sort**:

  * O(N log N), Stable 하지 않음

---

### 7. BBST

* **Red-Black Tree 균형 유지**:

  * 색상 규칙 및 회전 통해 log N 유지
* **성질**:

  1. 루트는 검정
  2. 빨간 노드는 연속되지 않음
  3. 모든 경로의 검정 노드 수 동일
  4. NIL은 검정
* **왜 Red-Black?**:

  * 균형 유지가 더 느슨해서 삽입/삭제 속도 빠름

---

### 8. 정렬 알고리즘

* **Quick vs Merge**:

  * Quick: 평균 O(N log N), 제자리, 불안정
  * Merge: O(N log N), 안정적, 공간 추가 필요
* **Quick의 최악 케이스**:

  * 정렬된 입력 → Pivot 선택 개선 (무작위/Median)
* **Stable Sort**: 같은 값의 순서 보존

  * Merge, Insertion, Bubble
* **Radix Sort**: 자릿수 기반, O(N)
* **Bubble/Selection/Insertion 비교**:

  * 모두 O(N^2), 정렬된 경우 Insertion이 가장 빠름
* **정렬 알고리즘 (Python)**: Timsort (Hybrid of Merge + Insertion)
* **외부 정렬 (50GB, 4GB 메모리)**:

  * 분할 후 정렬 + 병합 (External Merge Sort)

---

### 9. 그래프

* **인접행렬 vs 인접리스트**:

  * 연결 확인: O(1) vs O(degree)
  * 인접 노드 탐색: O(N) vs O(degree)
  * 공간: O(N^2) vs O(N+E)
* **간선 수가 N³ → 인접행렬**
* **사이클 없는 그래프 ≠ 트리**:

  * 연결 안 되어 있으면 포레스트

---

### 10. 최단거리

* **트리에서 최단거리**:

  * DFS 또는 BFS
* **다익스트라에서 힙 미사용**:

  * O(V²)
* **간선 N³ → Floyd-Warshall 적합 (O(N³))**
* **A**\*:

  * 휴리스틱 사용, 다익보다 빠름 (조건에 따라)
* **음수 간선/사이클**:

  * 간선만: Bellman-Ford
  * 사이클 포함: 탐지 및 종료 필요

---

### 11. 재귀함수

* **Call Stack 설명**:

  * 함수 호출 시 Stack Frame 생성 → 복귀 시 제거
* **Tail Recursion**:

  * 마지막 연산이 재귀 → 최적화 가능 (일부 언어만 지원)

---

### 12. MST

* **Union-Find**:

  * 경로 압축 + union by rank
* **Kruskal vs Prim**:

  * 희소 그래프: Kruskal
  * 밀집 그래프: Prim (Heap 활용)
* **MST는 항상 트리인가?**: 예, 모든 노드를 최소 비용으로 연결하며 사이클 없음

---

### 13. Thread Safe

* **없는 경우**:

  * 락, 뮤텍스, CAS 등 사용
* **배열 길이 이용**:

  * pre-allocated space를 이용한 lock-free 큐
* **Java**:

  * 기본 HashMap은 비안전, `ConcurrentHashMap` 제공

---

### 14. 문자열 알고리즘

* **Trie**: 접두어 검색 O(L)
* **KMP**: 접두사 배열 → O(N+M)
* **Rabin-Karp**: 해시 기반 → O(N), 충돌 발생 시 비교

---

### 15. 이진탐색

* **시간복잡도 증명**:

  * 반씩 줄어듦 → O(log N)
* **Lower/Upper Bound**:

  * Lower: 처음 등장하는 위치
  * Upper: 초과 첫 위치
* **삼진탐색 → O(log₃N)** (실제 효율은 이진보다 낮음)
* **부등호 변경 → 결과 달라짐**

---

### 16. 그리디 vs DP

* **그리디**:

  * 현재 최선 선택 → 전체 최선 (예: 활동 선택, Kruskal)
* **DP**:

  * Overlapping Subproblem + Optimal Substructure
* **DP → 재귀 변환**: 가능 (Memoization 활용)

---
