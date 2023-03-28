## 문제 설명
<p>JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다. 단, 첫 문자가 알파벳이 아닐 때에는 이어지는 알파벳은 소문자로 쓰면 됩니다. (첫 번째 입출력 예 참고)<br>
문자열 s가 주어졌을 때, s를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.</p>

## 제한사항
<ul>
<li>s는 길이 1 이상 200 이하인 문자열입니다.</li>
<li>s는 알파벳과 숫자, 공백문자(" ")로 이루어져 있습니다.

<ul>
<li>숫자는 단어의 첫 문자로만 나옵니다.</li>
<li>숫자로만 이루어진 단어는 없습니다.</li>
<li>공백문자가 연속해서 나올 수 있습니다.</li>
</ul></li>
</ul>

## 입출력 예
<table class="table">
        <thead><tr>
<th>s</th>
<th style="text-align: center">return</th>
</tr>
</thead>
        <tbody><tr>
<td>"3people unFollowed me"</td>
<td style="text-align: center">"3people Unfollowed Me"</td>
</tr>
<tr>
<td>"for the last week"</td>
<td style="text-align: center">"For The Last Week"</td>
</tr>
</tbody>
      </table>

# 문제 풀이
```java
class Solution {
    public String solution(String s) {
        String answer = "";

        String[] arr = s.split(" ");
        for(int i=0; i<arr.length; i++) {
            if(arr[i].length() == 0) continue;
            else {
                String tmp1 = arr[i].substring(0,1);
                String tmp2 = arr[i].substring(1);
                arr[i] = tmp1.toUpperCase() +tmp2.toLowerCase();
            }
        }

        answer = String.join(" ", arr);
        if(s.charAt(s.length()-1) == ' ') return answer + " ";
        return answer;
    }
}
```

# Comment
처음 문제를 풀었을 때 마지막 문자열이 공백일 경우를 생각하지 않아서 테스트케이스 8번만 계속 통과를 하지 못하였다
if(s.charAt(s.length()-1) == ' ') return answer + " "; 부분을 추가하여 정답코드로 인정받을 수 있었다.