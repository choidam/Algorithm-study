## 문제
- 프로그래머스 월간 코드 챌린지 시즌1 : 3진법 뒤집기
- https://programmers.co.kr/learn/courses/30/lessons/68935

<br/>

## 풀이
- 10진법을 3진법으로 뒤집어 변환한 후, 다시 10진법으로 변환하는 간단한 문제
- 제곱수를 구하는 `pow(n1, n2)` 를 처음 사용했다. 기억해두자!
- `char` 형을 `int` 형으로 변환하려면 `a-'0'` 을 사용하면 된다.


<br/>


## 코드

```c++
#include <string>
#include <vector>
#include <cmath>

using namespace std;

int solution(int n) {
    int answer = 0;
    
    // 앞 뒤 반전 3진법 변환
    string base3str = "";
    while(n>0){
        int tmp = n%3;
        n/=3;
        base3str += to_string(tmp);
    }
    
    // 3진수 -> 10진수 변환
    int mulnum = 0; // 지수
    for(int i=base3str.length()-1; i>=0; i--){
        int num = base3str[i]-'0'; // char to int
        int tmp = pow(3, mulnum);
        mulnum++;
        if(num>0){
            answer += num*tmp;
        }
    }
    
    return answer;
}
```

<br/>

## screenshot

<div align="center"><img src="./screenshots/prog_3진법뒤집기.png" width="500"></div>

<br/>
