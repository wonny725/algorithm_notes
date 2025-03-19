# 📚 [전화번호 목록]
> 플랫폼: [프로그래머스]  
> 난이도: [중]  
> 문제 유형: [해시]  
> 풀이 날짜: [2025.03.19]

---

## ✅ 문제 설명
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/42577)

---

## 🔍 **접근 방법**
- 비슷한 번호끼리 비교하려고 정렬
- 뒤랑 앞만 비교해도 됨
- i + 1이 있기 때문에 length - 1 해주기

---

## 💻 **내 코드**
```java
import java.util.*;

class Solution {
    public boolean solution(String[] phone_book) {
        Arrays.sort(phone_book);
        
        for (int i = 0; i < phone_book.length - 1; i++){
            if (phone_book[i + 1].startsWith(phone_book[i])){
                return false;
            }
        }
        return true;
    }
}
```
---

## 💻 **참조 코드**
```java
import java.util.HashSet;

class Solution {
    public boolean solution(String[] phone_book) {
        HashSet<String> set = new HashSet<>();
        for(String phone : phone_book) {
            set.add(phone); // 전화번호를 HashSet에 추가
        }

        for(String phone : phone_book) {
            for (int i = 1; i < phone.length(); i++) { // 부분 문자열 생성
                if(set.contains(phone.substring(0, i))){
                    return false;
                }
            }
        }
        return true;
    }
}
```