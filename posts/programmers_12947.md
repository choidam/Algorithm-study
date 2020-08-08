## 문제
- 프로그래머스 : 하샤드수
- https://programmers.co.kr/learn/courses/30/lessons/12947

<br/>

## 풀이
- 풀이 쓰기도 민망한 .. ㅎㅎ 각 자리 숫자를 더할 수 있으면 바로 풀 수 있는 문제

<br/>

## 코드

```c++
using namespace std;

bool solution(int x) {
    int hashad = 0;
    int num = x;
    
    while(x>0){
        int tmp = x%10;
        hashad += tmp;
        x/=10;
    }
    
    if(num%hashad==0)
        return true;
    else
        return false;
}
```

<br/>

## screenshot

<img src="./screenshots/prog_하샤드.png" width="500">

