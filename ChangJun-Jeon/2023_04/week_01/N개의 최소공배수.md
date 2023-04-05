# 문제
https://school.programmers.co.kr/learn/courses/30/lessons/12953

두 정수가 아닌 임의의 정수 N개의 최소 공배수를 구하는 문제였다.

가장 먼저 떠오른 방법은 0번째 1번째의 최대 공약수를 구하고, 이를 통해 두 수의 최소 공배수 x를 구한다면

이어지는 다음 정수와 N[i]와 x를 매치 시켜 N개의 최소 공배수를 구할 수 있을거같았다.

# 문제 풀이

```java
class Solution {
    public int solution(int[] arr) {
        int answer = 0;
        // 0. 유클리드 호제법 사용 - 배열의 0-1번의 최대 공약수를 구한다.
        int gcd = GCD(arr[0], arr[1]);
        
        // 1. 배열의 0-1번의 최소 공배수 구한다.
        int lcm = (arr[0] * arr[1])/gcd;
        
        // 2. 0-1번의 최소 공배수와 2-n번의 최대 공약수, 최소 공배수를 구한다.
        for(int i=2; i<arr.length; i++){
            gcd = GCD(lcm, arr[i]);
            lcm = (lcm * arr[i])/gcd;
        }
        answer = lcm;
        
        return answer;
    }
    
    public int GCD(int x, int y){
        if(y == 0) return x;
        else return GCD(y, x%y);
    }
}

```

# Comment

공식을 그대로 적용해서 풀이했다. 최소 공배수, 최대 공약수를 구하는 공식 - 유클리드 호제법
