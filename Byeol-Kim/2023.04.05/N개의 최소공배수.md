## 접근

유클리드 호제법을 이용하면 된다.

## 풀이
```
class Solution {
    public int solution(int[] arr) {
        int answer = 0;
     
        
        for(int i=1;i<arr.length;i++){
            int A = arr[i-1];
            int B = arr[i];
            //유클리드 호제법을 통해서 최대공약수 구하기
            int min = gcd(A>B?A:B,A>B?B:A);
            // arr[i] = A와 B의 최소공배수가 저장된다.
            arr[i] = A*B/min;
        }
        
        
        return answer= arr[arr.length-1];
    }
    //유클리드 호제법 이용
    static int gcd(int A, int B){
        if(B==0) return A;
        return gcd(B,A%B);
    }
    
    
}
```