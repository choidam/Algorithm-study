## 문제
- 프로그래머스 : 124 나라의 숫자
- https://programmers.co.kr/learn/courses/30/lessons/12899

<br/>

## 풀이
- 3진수 숫자 구하기와 비슷한 맥락의 문제 
- 나머지가 0인 경우 ``` n/3 - 1 ``` 으로 값을 맞춰줘야 한다.


<br/>


## 코드

```c++
#include <string>

using namespace std;

string solution(int n) {
    string answer = "";
    
    int left; // 나머지
    
    while(n != 0){
        left = n % 3;
        if(left == 0){
            answer.insert(0, "4");
            n = n/3 - 1;
        } else{
            answer.insert(0, to_string(left));
            n /= 3;
        }
    }
    
    
    return answer;
}
```



<br/>

## screenshot

<img src="./screenshots/prog_124_나라의숫자.png" width="600" height="280">


<br/>
