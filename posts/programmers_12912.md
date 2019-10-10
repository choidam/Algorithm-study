## 문제
- 프로그래머스 : 12912
- https://programmers.co.kr/learn/courses/30/lessons/12912

## 풀이
- min, max 값 정하고 더하기만 하면 된다!

## 코드
```c++
#include <string>
#include <vector>

using namespace std;

long long solution(int a, int b) {
    long long answer = 0;
    long long min, max;
    
    if(a>b) { max=a;min=b;}
    else{ max=b;min=a;}
    
    for(long long i=min; i<=max; i++){
        answer += i;
    }

    return answer;
}
```

## screenshot
![screenshot](./screenshots/prog_12912.png)

## 참고자료
- 없음
