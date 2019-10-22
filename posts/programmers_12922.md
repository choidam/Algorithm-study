## 문제
- 프로그래머스 : 수박수박수박수박수?
- https://programmers.co.kr/learn/courses/30/lessons/12922

<br/>

## 풀이
- string.appendd(); 만 안다면 1분 만에 풀 수 있는 문제.

<br/>

## 코드

```c
#include <string>

using namespace std;

string solution(int n) {
    string answer = "";
    
    for(int i=1; i<=n; i++){
        if(i%2==1){
            answer.append("수");
        } else {
            answer.append("박");
        }
    }
    
    return answer;
}
```

<br/>

## screenshot

![screenshot](./screenshots/prog_수박수.png)
