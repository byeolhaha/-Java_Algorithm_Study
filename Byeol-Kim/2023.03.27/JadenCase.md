## 접근
>https://school.programmers.co.kr/learn/courses/30/lessons/12951#

문자열 s가 입력값으로 들어온다.
단어의 첫문자는 대문자
그 외 알파벳은 소문자이다.

문자열 s는 알파벳, 숫자, 공백문자로 이루어져 있고
숫자는 첫문자로만 등장, 숫자로만 이루어진 단어는 없다.
또한 공백은 한칸일 수도 있고 연속해서 여러칸이 등장할 수도 있다.

이 문제는 여러가지 테스트케이스를 스스로 생각해봐야 했다.
- 끝에도 공백이 있을 수도 있다.
- 마찬가지로 앞에도
- 그리고 공백이 한칸이 아니라 여러칸일 수도 있다.

마지막으로 다른 분의 코드가 더 간결했기 때문에 문제를 좀 더 쉽게 풀어나가는 방법을 배워야할거 같다.

## 과정

- 문자열을 단어별로 자르는 과정
 ```java
String[] s_arr = s.split(" ");
 ```
 여기서 생각해볼 것이 " "한칸으로 나눴다는 것
 따라서 **"  3  "을 "","","3"으로 나눈다는 사실**을 기억하자!!!


- 첫문자를 대문자로 바꾸는 과정
 ```java
 for(String s_value : s_arr){
            if(s_value.equals("")){
                side_answer.append(" ");
                continue;
            }
            int v = (int)s_value.charAt(0); 
            String first = (s_value.charAt(0)+"");
            if((v>=97&& v<=122)) {
               first = (s_value.charAt(0)+"").toUpperCase();
            } 
            s_value = first+ s_value.substring(1).toLowerCase();
            
            side_answer.append(s_value+" ");  
         }
 ```
- 마지막에 뒤에 있었던 공백은 추가하는 과정
 ```java
 for(String s_value : s_arr){
  ...
  side_answer.append(s_value+" ");  
  }

 //뒤 공백 제거
        String answer = side_answer.toString().stripTrailing();
        
        //끝에 공백 추가
        int blank = s.length()- answer.length();
        for(int i=0;i<blank;i++){
            answer+=" ";
        }
 ```
   - for문을 통해서 s_arr에 각 값들이 ""이 아닌경우 " "을 추가했다.
 따라서 for문을 벗어나면 쓸데없는 마지막 공백" "이 추가되기 때문에 빼줬다. 즉 "123 234"인데 "123 234 "이렇게 저장된다.
   - 또한 split()의 경우 "  3  "앞 공백에 대해서만 고려하기 때문에 뒤의 공백은 
   ```java
   int blank = s.length()- answer.length();
        for(int i=0;i<blank;i++){
            answer+=" ";
        }
  ```
  위와 같은 과정을 거쳐 추가한다.


## 풀이(java)
```
class Solution {
    public String solution(String s) {
    
        StringBuilder side_answer = new StringBuilder();
        

        String[] s_arr = s.split(" ");

        
        for(String s_value : s_arr){
            if(s_value.equals("")){
                side_answer.append(" ");
                continue;
            }
            int v = (int)s_value.charAt(0); 
            String first = (s_value.charAt(0)+"");
            if((v>=97&& v<=122)) {
               first = (s_value.charAt(0)+"").toUpperCase();
            } 
            s_value = first+ s_value.substring(1).toLowerCase();
            
            side_answer.append(s_value+" ");  
        }
        
        //뒤 공백 제거
        String answer = side_answer.toString().stripTrailing();
        
        //끝에 공백 추가
        int blank = s.length()- answer.length();
        for(int i=0;i<blank;i++){
            answer+=" ";
        }
        
        return answer;
    }
}
```
## 다른 사람의 더 간단한 풀이
```java
import java.util.*;
import java.io.*;

class Solution {
    public String solution(String s) {
        //JadenCase 첫문자 대문자, 그외 소문자인 문자열
        //아닌 경우 이어지는 문자는 소문자
        //s 길이 1~200
        //숫자는 단어의 첫 문자로만 나온다.
        //공백문자는 연속해서 나올 수 있다.
        
        String answer="";
         
        String[] s_arr = s.toLowerCase().split("");
         
        boolean tag = true;
        for(String s_value : s_arr){
           
             answer+=tag?s_value.toUpperCase():s_value;
             tag=s_value.equals(" ")?true:false;
          
        }
      
        
        return answer;
    }
}
```
더 간결하게 풀 수 있었다.
모두 소문자로 바꾼 후에 
split("")로 하면 공백도 함께 배열 index 값으로 저장된다.
