# 📚 [문제 제목] - [문제 번호 또는 링크]
> 플랫폼: [프로그래머스]  
> 난이도: [중]  
> 문제 유형: [스택큐]  
> 풀이 날짜: [2025.03.17]

---

## ✅ 문제 설명
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/42583?language=java)

---

## 🔍 **접근 방법**
- 처음 문제를 어떻게 접근했는지, 고려한 점을 작성  
- 문제를 풀 때 생각한 로직 정리  
- 시간 복잡도, 공간 복잡도 고려 사항

---

## 💻 **풀이 코드** (성공 or 실패)
```java
# 여기에 코드 입력
import java.util.*;

class Solution {
    public int solution(int bridge_length, int weight, int[] truck_weights) {
        int time = 0; // 경과 시간
        int currentWeight = 0; // 다리 위에 있는 트럭들의 무게 합
        Queue<Integer> bridge = new LinkedList<>(); // 다리 위에 있는 트럭들을 나타내는 큐

        // 초기화: 다리 길이만큼 0으로 채움 (트럭이 없는 상태)
        for (int i = 0; i < bridge_length; i++) {
            bridge.offer(0);
        }

        int truckIndex = 0; // 대기 중인 트럭의 인덱스
        while (truckIndex < truck_weights.length) {
            time++; // 시간 증가

            // 1. 다리에서 트럭 내보내기 (맨 앞 트럭 제거)
            currentWeight -= bridge.poll();

            // 2. 다리에 트럭 올리기 (조건 확인 후)
            if (currentWeight + truck_weights[truckIndex] <= weight) {
                // 다리에 여유 공간이 있으면 새 트럭 추가
                bridge.offer(truck_weights[truckIndex]);
                currentWeight += truck_weights[truckIndex];
                truckIndex++;
            } else {
                // 다리에 여유 공간이 없으면 0 추가 (트럭 이동 효과)
                bridge.offer(0);
            }
        }

        // 마지막 트럭이 다리에 올라간 후, 다리를 통과하는 시간 추가
        time += bridge_length;

        return time;
    }
}