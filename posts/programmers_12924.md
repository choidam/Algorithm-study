## 문제
- 프로그래머스 : 숫자의표현
- https://programmers.co.kr/learn/courses/30/lessons/12924

<br/>

## 풀이
- 마음 편히 푼 문제 ㅎ.ㅎ
- 각 정수에 대해 숫자의 총합 sum 이 n보다 커질 때까지 while문을 돌렸다. 
- while 문 탈출 시 숫자가 n과 같을 경우 answer 증가! 

<br/>


## 코드

```c++
using namespace std;

int solution(int n) {
    int answer = 1;
    
    for(int i=1; i<=n/2; i++){
        int tmp = i;
        int sum = 0;
        while(sum<n){
            sum += tmp;
            tmp++;
        }
        if(sum == n){
            answer++;
        }
    }
    return answer;
}
```



<br/>

## screenshot

<img src="./screenshots/prog_숫자의표현.png" width="600" height="280">


<br/>
