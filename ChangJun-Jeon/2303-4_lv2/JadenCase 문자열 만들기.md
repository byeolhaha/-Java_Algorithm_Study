# 문제 설명

JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다. 단, 첫 문자가 알파벳이 아닐 때에는 이어지는 알파벳은 소문자로 쓰면 됩니다. (첫 번째 입출력 예 참고)
문자열 s가 주어졌을 때, s를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.

## 제한 조건

s는 길이 1 이상 200 이하인 문자열입니다.
s는 알파벳과 숫자, 공백문자(" ")로 이루어져 있습니다.
숫자는 단어의 첫 문자로만 나옵니다.
숫자로만 이루어진 단어는 없습니다.
공백문자가 연속해서 나올 수 있습니다.

## 입출력 예
<img width="424" alt="Screenshot 2023-03-27 at 5 22 22 PM" src="https://user-images.githubusercontent.com/86146128/227883843-b9af56d6-23f9-446a-861b-c1b161da2e01.png">


## 문제 풀이

```
class Solution {
    public String solution(String s) {
        String answer = "";
        char before = ' ';
        for(char c : s.toCharArray()){
            if(Character.isDigit(c) || c == ' ') answer += c;
            else {
                answer += before == ' ' ? Character.toUpperCase(c) : Character.toLowerCase(c);
            }
            before = c;
        }
        return answer;
    }
}
```

# Comment
같이 스터디를 진행하는 희나님 코드를 참고했다.
여러 방법을 도전해봤지만 풀 수 없었는데, 과거에 같은 문제를 풀고 단어 중간에 공백이 포함되어있으면 어떻게 처리할지 고민하느라
테스트 케이스를 추가해놨던걸 잊어버려서 모두 오답이 됐다..
