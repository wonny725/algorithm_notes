# 📚 [폰켓몬]
> 플랫폼: [프로그래머스]  
> 난이도: [하]  
> 문제 유형: [해시]  
> 풀이 날짜: [2025.03.17]

---

## ✅ 문제 설명
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/1845)

---

## 🔍 **접근 방법**
- 중복 제거 -> HashSet 사용
- Math.min 사용

---

## 💻 **내 코드**
```java
import java.util.*;

class Solution {
    public int solution(int[] nums) {
        HashSet<Integer> mons = new HashSet<>();
        for (int num : nums){
            mons.add(num);
        }
        
        return Math.min(nums.length / 2, mons.size());
    }
}
```
---

## 💻 **고수 코드**
```java
import java.util.Arrays;
import java.util.stream.Collectors;

class Solution {
    public int solution(int[] nums) {
        return Math.min(nums.length / 2, Arrays.stream(nums)
                .boxed()
                .collect(Collectors.toSet()).size());
    }
}
```