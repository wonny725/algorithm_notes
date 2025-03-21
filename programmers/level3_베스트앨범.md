# 📚 [베스트앨범]
> 플랫폼: [프로그래머스]  
> 난이도: [상]  
> 문제 유형: [해시]  
> 풀이 날짜: [2025.03.21]

---

## ✅ 문제 설명
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/42579)

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
import java.util.*;

class Solution {
    public int[] solution(String[] genres, int[] plays) {
        // 1. 장르별 총 재생 횟수 계산
        HashMap<String, Integer> genrePlayCount = new HashMap<>();
        for (int i = 0; i < genres.length; i++) {
            genrePlayCount.put(genres[i], genrePlayCount.getOrDefault(genres[i], 0) + plays[i]);
        }

        // 2. 장르별 총 재생 횟수를 기준으로 내림차순 정렬 (장르 순서 결정)
        List<String> genreOrder = new ArrayList<>(genrePlayCount.keySet());
        Collections.sort(genreOrder, (a, b) -> genrePlayCount.get(b) - genrePlayCount.get(a));

        // 3. 결과 리스트 생성 (베스트 앨범에 들어갈 노래 고유번호)
        List<Integer> bestAlbum = new ArrayList<>();

        // 4. 정렬된 장르 순서대로 순회
        for (String genre : genreOrder) {
            // 5. 해당 장르 내에서 노래 선별
            List<Song> songsInGenre = new ArrayList<>();
            for (int i = 0; i < genres.length; i++) {
                if (genres[i].equals(genre)) {
                    songsInGenre.add(new Song(i, plays[i])); // 노래 고유번호, 재생 횟수
                }
            }

            // 6. 해당 장르 내에서 재생 횟수 내림차순, 고유번호 오름차순 정렬
            Collections.sort(songsInGenre, (a, b) -> {
                if (a.playCount != b.playCount) {
                    return b.playCount - a.playCount; // 재생 횟수 내림차순
                }
                return a.id - b.id; // 고유번호 오름차순
            });

            // 7. 베스트 앨범에 최대 2곡 추가
            bestAlbum.add(songsInGenre.get(0).id); // 첫 번째 노래 추가
            if (songsInGenre.size() > 1) {
                bestAlbum.add(songsInGenre.get(1).id); // 두 번째 노래 추가 (있으면)
            }
        }

        // 8. List<Integer>를 int[]로 변환
        int[] answer = new int[bestAlbum.size()];
        for (int i = 0; i < bestAlbum.size(); i++) {
            answer[i] = bestAlbum.get(i);
        }
        return answer;
    }

    // 노래 정보를 저장할 내부 클래스
    class Song {
        int id;       // 노래 고유 번호
        int playCount; // 재생 횟수

        public Song(int id, int playCount) {
            this.id = id;
            this.playCount = playCount;
        }
    }
}
```