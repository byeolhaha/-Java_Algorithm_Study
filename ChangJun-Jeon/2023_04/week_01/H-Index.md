# 문제

https://school.programmers.co.kr/learn/courses/30/lessons/42747?itm_content=course14743

문제를 이해하는데 너무 오래 걸렸다. 

논문 n편 중, h번 이상 인용된 논문이 h편 이상이고 나머지 논문이 h번 이하 인용되었다면 h의 최댓값이 H-Index입니다.

--> 논문 n편이 있다면 h번 이상 인용된 논문이 h편 이상이다.
  -> 논문 n편 : 주어진 배열 길이
  -> h번 이상 : h번 이상이라는것은 전체 배열 길이와 논문[i]를 통해 구해야한다.

# 문제 풀이 - 실패 코드 (단순 중앙값 계산)

```java

import java.util.*;
class Solution {
    public int solution(int[] citations) {
        int answer = 0;
        int mda = median(citations);
        for(int x : citations){
            if (x >= mda) answer++;
        }
        return answer;
    }
    // 0 1 3 5 6
    public int median(int[] arr){
        Arrays.sort(arr);
        int result;
        if(arr.length % 2 == 0){
            int pos = arr.length/2;
            int pre = arr.length/2 - 1;
            result = (arr[pos] + arr[pre]) / 2;
        }else result = arr[arr.length/2];
        return result;
    }
}

```

# 문제 풀이 - 성공 코드

```java
import java.util.*;
class Solution {
    public int solution(int[] citations) {
        Arrays.sort(citations);
        
        int n = citations.length;
        int idx = 0;
        
        for(int i=0; i<n; i++){
            int num_papers = n-i;
            if(citations[i] >= num_papers){
                idx = num_papers;
                break;
            }
        }
        return idx;
    }
}
```
