# 📚 [네트워크]
> 플랫폼: [프로그래머스]  
> 난이도: [상]  
> 문제 유형: [dfs/bfs]  
> 풀이 날짜: [2025.03.21]

---

## ✅ 문제 설명
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/43162)

---

## 🔍 **접근 방법**
- 좀 복잡해짐

---

## 💻 **내 코드**
```java
```
---

## 💻 **참조 코드**
```java
// 정석 풀이 (DFS - 재귀)
class Solution {
    public int solution(int n, int[][] computers) {
        int answer = 0; // 네트워크 개수
        boolean[] visited = new boolean[n]; // 방문 여부 체크 배열

        // 모든 컴퓨터(노드)를 순회하면서
        for (int i = 0; i < n; i++) {
            // 아직 방문하지 않은 컴퓨터라면, DFS 탐색 시작
            if (!visited[i]) {
                dfs(i, computers, visited);
                answer++; // DFS 탐색이 끝나면 네트워크 개수 증가
            }
        }

        return answer;
    }

    // DFS 함수 (재귀)
    private void dfs(int node, int[][] computers, boolean[] visited) {
        visited[node] = true; // 현재 노드 방문 처리

        // 현재 노드와 연결된 다른 노드들을 순회
        for (int i = 0; i < computers.length; i++) {
            // 연결되어 있고, 아직 방문하지 않은 노드라면 DFS 재귀 호출
            if (computers[node][i] == 1 && !visited[i]) {
                dfs(i, computers, visited);
            }
        }
    }
}
```