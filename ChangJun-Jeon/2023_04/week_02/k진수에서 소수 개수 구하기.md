# 문제 

https://school.programmers.co.kr/learn/courses/30/lessons/92335


# 문제 풀이

```java

class Solution {
    public int solution(int n, int k) {
        int answer = 0;
        // 0을 기준으로 배열 만들기
        // Integer.toString(n,k) --> 정수 n을 k진수로 String 타입 반환 메서드
        String[] trans_num = Integer.toString(n,k).split("0");
        
        for(String x : trans_num){
            // 비어있거나, 1의 경우를 제외
            if(!x.equals("") && !x.equals("1")){
                // 소수 판별
                boolean temp = isPrime(Double.valueOf(x));
                if (temp) answer++;
            }
        }
        return answer;
    }
    
    public boolean isPrime(double n){
        for(int i=2; i<=(int)Math.sqrt(n); i++)
            if(n % i == 0) return false;
        
        return true;
    }
}

```
# Comment

진법 변환을 할 수 있는지, 소수 판별을 할 수 있는지에 대한 문제였다.

테스트 케이스 1번에서 몇 번 실패했는데, 이는 String으로 변환된 k진수를 정수로 변환할 때 크기가 int 범위를 넘어가기 떄문이었다.


