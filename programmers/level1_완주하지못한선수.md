# 📚 [완주하지 못한 선수]
> 플랫폼: [프로그래머스]  
> 난이도: [하]  
> 문제 유형: [해시]  
> 풀이 날짜: [2025.03.17]

---

## ✅ 문제 설명
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/42576)

---

## 🔍 **접근 방법**
- key, value HashMap 사용
- getOrDefault 중복 체크 (x, 0)
- value값 비교 후 key return

---

## 💻 **내 코드**
```java
import java.util.*;

class Solution {
    public String solution(String[] participant, String[] completion) {
        Arrays.sort(participant);
        Arrays.sort(completion);
        
        for (int i = 0; i < completion.length; i++){
            if (!participant[i].equals(completion[i])){
                return participant[i];
            }
        }
        
        return participant[participant.length - 1];
    }
}
```
---

## 💻 **참조 코드**
```java
import java.util.HashMap;

class Solution {
    public String solution(String[] participant, String[] completion) {
        HashMap<String, Integer> map = new HashMap<>();

        // 참가자 명단을 HashMap에 추가 (이름, 등장 횟수)
        for (String p : participant) {
            map.put(p, map.getOrDefault(p, 0) + 1);
        }

        // 완주자 명단을 HashMap에서 제거
        for (String c : completion) {
            map.put(c, map.get(c) - 1);
        }

        // HashMap에서 value가 0이 아닌 key(이름)를 찾아서 반환
        for (String key : map.keySet()) {
            if (map.get(key) != 0) {
                return key;
            }
        }
        return ""; // 예외 처리 (문제 조건 상 발생하지 않음)
    }
}
```