# 📚 [주식가격]
> 플랫폼: [프로그래머스]  
> 난이도: [중]  
> 문제 유형: [스택큐]  
> 풀이 날짜: [2025.03.17]

---

## ✅ 문제 설명
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/42584)

---

## 🔍 **접근 방법**
- Stack에 index 넣고 비교
- answer에다가 기간 계산 넣기
- 끝까지 가격 안떨어지는 인덱스도 계산

---

## 💻 **내 코드**
```java
import java.util.*;

class Solution {
    public int solution(int bridge_length, int weight, int[] truck_weights) {
    }
}
```
---

## 💻 **참조 코드**
```java
import java.util.Stack;

class Solution {
    public int[] solution(int[] prices) {
        int[] answer = new int[prices.length];
        Stack<Integer> stack = new Stack<>(); // 주식 가격의 인덱스를 저장할 스택

        for (int i = 0; i < prices.length; i++) {
            // 스택이 비어있지 않고, 현재 가격이 스택 top의 가격보다 떨어졌으면
            while (!stack.isEmpty() && prices[i] < prices[stack.peek()]) {
                int topIndex = stack.pop(); // 스택에서 인덱스를 꺼냄
                answer[topIndex] = i - topIndex; // 가격이 떨어지지 않은 기간 계산
            }
            stack.push(i); // 현재 가격의 인덱스를 스택에 넣음
        }

        // 스택에 남아있는 인덱스들은 끝까지 가격이 떨어지지 않은 경우
        while (!stack.isEmpty()) {
            int topIndex = stack.pop();
            answer[topIndex] = prices.length - 1 - topIndex; // 전체 길이 - 1 - 인덱스
        }

        return answer;
    }
}
```