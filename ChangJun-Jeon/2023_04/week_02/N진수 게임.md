# 문제

https://school.programmers.co.kr/learn/courses/30/lessons/17687

# 문제 풀이

```java
class Solution {
    public String solution(int n, int t, int m, int p) {
        StringBuilder sb = new StringBuilder();
        int num = 0; // 하나씩 늘림
        int idx = 0; // 몇번째 차례인지
        
        // 1. n 진법으로 변환해야할 수(num)를 1씩 늘리면서 계산한다.
        while(true){
            // t 개 이상 구했다면 종료
            if(sb.length() >= t) break;
            // 1.1. num을 n진법 변환
            String convert = Integer.toString(num, n);
            // 1.2. 차례를 1씩 증가시키면서 튜브의 차례이면 i번째 위치의 문자를 정답에 넣는다.
            for(int i=0; i<convert.length(); i++){
                if(idx % m + 1 == p) {
                    sb.append(convert.charAt(i));
                    // System.out.println(sb.toString());
                    }
                idx++;
            }
            // 1.3. num + 1이 다음으로 변환해야할 숫자이다.
            num++;
        }
        // 2. t 길이만큼 반환
        return sb.substring(0,t).toUpperCase();
    }
}
```

# Comment

문제 파악이 어려워 희나님 코드를 보고 이해했다.

![Screenshot 2023-04-15 at 7 14 06 PM](https://user-images.githubusercontent.com/86146128/232207913-70917de2-3186-4aa7-af6b-47b44703ab8a.png)

튜브의 차례일때마다 빌더에 하나씩 새로운 문자가 추가되고, 미리 구할 숫자의 개수 t가 충족되면 종료되는 방식이다.
