## 문제
- 프로그래머스 Summer/Winter coding(~2018) - 점프와 순간 이동
- https://programmers.co.kr/learn/courses/30/lessons/12980

<br/>

## 풀이
- DP 문제라고 생각해서 처음엔 점화식을 막 썼는데 ,, 거꾸로 생각하면 매우 간단하게 풀 수 있는 문제다.
- 짝수인 경우 순간이동을, 홀수인 경우 한 칸 점프를 해주며 0이 될 때까지 무한루프를 돌린다.

<br/>

## 코드

```c++
#include <iostream>
using namespace std;

int solution(int n)
{
    int ans = 0;
    
    while(n!=0){
        if(n%2==0){
            n/=2;
        } else {
            n--;
            ans++;
        }
    }
    return ans;
}
```

<br/>

## screenshot

<img src="./screenshots/prog_점프.png" width="500">

