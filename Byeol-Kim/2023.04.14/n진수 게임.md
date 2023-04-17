## 접근
>https://school.programmers.co.kr/learn/courses/30/lessons/17687

이 문제는 아이디어를 떠올리지 못해서 실패했습니다.

다른 분의 풀이를 보고 힌트를 얻어 풀었습니다.
여기서 Integer.toString()이 단순히 Integer를 문자열로 바꿔주는 역할만이 아니라
십진수의 값을 n진수의 문자열로 바꿔주는 역할도 한다는 것을 알게 되었습니다.

```
String str = Integer.toString(int ten, int n);
//ten은 십진수 -> n진수의 문자열로
```

어떤 문자열을 처음에 빈 문자열로 둔 다음에
0부터 구하고자 하는 순서가 나올 때까지 수를 1씩 더하고 이를 n진수로 바꾼 문자열을 기존 문자열에 더하는 방법으로 접근했습니다.

## 풀이
```java
class Solution {
    public String solution(int n, int t, int m, int p) {
        String answer = "";
        
        int[] turn = new int[t];
        
        //순서저장
        turn[0]=p;
        for(int i=1;i<t;i++)
            turn[i]=turn[i-1]+m;
           
                    
        String newStr="";
        int index=0;
        for(int target : turn ){
            //길이가 작을 때까지 계속 숫자를 1씩 늘려가며 붙여나가기
            while(newStr.length()<target){
                newStr+=Integer.toString(index++,n);
            }
            //newStr의 자리수에 있는 값을 answer에 넣기
            answer+=newStr.charAt(target-1);         
        }
        
        
      answer= answer.toUpperCase();
      return answer;  
    }
}
```
