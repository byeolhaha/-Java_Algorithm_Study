## 접근
>https://school.programmers.co.kr/learn/courses/30/lessons/92335
크게 두가지 흐름으로 갑니다.
1. 십진수를 k진수로 바꾸기
2. 바꾼 수에서 0을 기준으로 숫자만 뽑기

## 풀이


```java
import java.util.*;

class Solution {
    public int solution(int n, int k) {
        int answer = 0;
        if(n==1) return 0;
        
        String N = make_k(n,k);
        answer = make_prime(N);
        
        
        return answer;
    }
    
    //진수 만들기
    static String make_k(int n,int k){
        String output="";
        //1. stack에 나머지들을 저장하기 위해
        Stack<String> st = new Stack<>();
        //2. n이 k보다 크거나 같을 때까지 돌립니다.
        while(n>=k){
        //3. 나머지는 stack에 넣어줍니다.
         st.add(Integer.toString(n%k));
        //4. 몫을 저장합니다.
         n=n/k;     
        }
        st.add(Integer.toString(n));
        
        //5.stack에 쌓이 나머지 꺼꾸로 쌓기
        while(st.size()>0){
           output+=st.pop(); 
        }
        return output;
           
    }
    
    //진수에서 소수 찾기
    static int make_prime(String N){
        
       
        //1. split메서드를 이용해서 "0"분리해서 숫자 넣기
        String[] digit = N.split("0");
        
        
        int cnt=0;
        
        //3. 숫자가 소수인지 확인하는 과정
        for(String d : digit){
            //빈값이나 1의 경우 continue;
            if(d.equals("")) continue;
            if(d.equals("1")) continue;
            //아닌 경우 소수인지 체크
            double D = Double.parseDouble(d);
            boolean tag = false;
            for(double i=2;i<=Math.sqrt(D);i++){
                if(D%i==0){
                    tag=true;
                    break;
                }
            }
            if(!tag) cnt++;
            
        }
       
        return cnt;
        
        
    }
    
    
}
```