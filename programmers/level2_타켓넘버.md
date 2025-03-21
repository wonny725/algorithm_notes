# 📚 [타켓넘버]
> 플랫폼: [프로그래머스]  
> 난이도: [중]  
> 문제 유형: [dfs/bfs]  
> 풀이 날짜: [2025.03.21]

---

## ✅ 문제 설명
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/43165)

---

## 🔍 **접근 방법**
- 좀 복잡해짐

---

## 💻 **내 코드**
```java
class Solution {
    int answer = 0;
    public int solution(int[] numbers, int target) {
        dfs(numbers, target, 0, 0);
        return answer;
    }
    
    private void dfs(int[] numbers, int target, int depth, int sum){
        if(depth == numbers.length){
            if(target == sum){
                answer++;
            }
            return;
        }
        dfs(numbers, target, depth + 1, sum + numbers[depth]);
        dfs(numbers, target, depth + 1, sum - numbers[depth]);
    }
}
```
---

## 💻 **참조 코드**
```java
//(BFS - 큐)

import java.util.LinkedList;
import java.util.Queue;

class Solution {
    public int solution(int[] numbers, int target) {
        int answer = 0;
        Queue<Node> queue = new LinkedList<>(); // BFS를 위한 큐
        queue.offer(new Node(0, 0)); // 초기값 (깊이 0, 합 0)을 큐에 넣음

        while (!queue.isEmpty()) {
            Node current = queue.poll(); // 큐에서 노드 하나를 꺼냄

            // 모든 숫자를 다 사용했는지 확인
            if (current.depth == numbers.length) {
                if (current.sum == target) { // 합이 타겟 넘버와 같으면
                    answer++; // 방법의 수 증가
                }
                continue; // 다음 노드 처리
            }

            // 현재 숫자를 더한 경우와 뺀 경우를 큐에 추가
            queue.offer(new Node(current.depth + 1, current.sum + numbers[current.depth]));
            queue.offer(new Node(current.depth + 1, current.sum - numbers[current.depth]));
        }

        return answer;
    }

    // 노드 정보를 저장할 내부 클래스
    class Node {
        int depth; // 현재 처리 중인 숫자의 인덱스 (깊이)
        int sum;   // 현재까지의 숫자들의 합

        public Node(int depth, int sum) {
            this.depth = depth;
            this.sum = sum;
        }
    }
}
```