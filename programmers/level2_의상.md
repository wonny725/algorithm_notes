# 📚 [의상]
> 플랫폼: [프로그래머스]  
> 난이도: [중]  
> 문제 유형: [해시]  
> 풀이 날짜: [2025.03.19]

---

## ✅ 문제 설명
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/42578)

---

## 🔍 **접근 방법**
- 옷 종류, 갯수 hashmap 만들기
- 2차원 배열 for -> (1차원 배열 : 2차원배열)
- 중복 시 카운트++ -> 종류 다른 카운트끼리 곱하고 안 입는 경우 -1

---

## 💻 **내 코드**
```java
import java.util.*;

class Solution {
    public int solution(String[][] clothes) {
        HashMap<String, Integer> map = new HashMap<>();

        for (String[] cloth : clothes) {
            String type = cloth[1];
            map.put(type, map.getOrDefault(type, 0) + 1);
        }

        int answer = 1;
        for (int count : map.values()) {
            answer *= (count + 1);
        }

        return answer - 1;
    }
}
```
---

## 💻 **참조 코드**
```java
import java.util.Arrays;
import java.util.stream.Collectors;

class Solution {
    public int solution(String[][] clothes) {
        return Arrays.stream(clothes)
                .collect(Collectors.groupingBy(p -> p[1], Collectors.counting())) // 의상 종류별로 그룹화하고 개수 세기
                .values().stream()
                .reduce(1L, (a, b) -> a * (b + 1)).intValue() - 1; // 각 (개수 + 1)을 곱하고 1 빼기
    }
}
```