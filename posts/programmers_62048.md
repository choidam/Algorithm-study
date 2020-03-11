## 문제
- 프로그래머스 : 서머코딩/윈터코딩(2019) 멀쩡한 사각형
- https://programmers.co.kr/learn/courses/30/lessons/62048

<br/>

## 풀이
gcd 를 w와 h의 최대 공약수라 할 때,
- 선이 지나가면서 겹치는 사각형 개수는 규칙적이다.
- 블록의 크기는 ```(w/gcd) x h(/gcd)``` 이다.
- 한 블록 안에서는 ```(블록의 가로 크기 + 블록의 세로 크기 -1)``` 수 만큼의 사각형 위로 선이 지나간다.

<br/> 

## 풀이

```c++
using namespace std;

long long solution(int w,int h)
{
    int gcd;
    long long sum = (long long)w * (long long)h;
    
    for(int i = (w<h) ? w : h; i>0; i--){
        if((w%i==0) && (h%i==0)){
            gcd = i;
            break;
        }
    }
    
    return sum - gcd*((w/gcd)+(h/gcd)-1);
}
```

<br/>

## screenshot

 <img src="./screenshots/prog_멀쩡한_사각형.png" width="600" height="380"> 
