## 접근
처음에 정렬을 하여 처음부터 index 값에 접근했지만
H-Index가 배열에 존재하는 값이 아닐 수도 있기 때문에 다시 완전 탐색으로 구현하였다.

## 풀이
```
import java.util.*;
class Solution {
    static int max = Integer.MIN_VALUE;
    public int solution(int[] citations) {
        
         //어떤 과학자가 발표한 논문 n (1~1000)
        //h번 이상 인용된 논문이 h편 이상 (인용 횟수 0~10000)
        // 나머지 논문이 h번 이하 인용
        //h의 최댓값
        
        // answer -1부터 시작
        int answer = -1;
        
        //1. 먼저 정렬하기
        Arrays.sort(citations);
        
        for(int i=0;i<citations.length;i++){
            while(true){
            // 2. answer+1을 했을 때 현재 논문의 인용횟수보다 크거나 같고
            // 남아있는 논문의 개수보다 작거나 같을 때 
            if(answer+1<=citations[i] && answer+1<=citations.length-i)
                answer++; 
            else break;
          }
        }
        
        return answer;
    }
}
```