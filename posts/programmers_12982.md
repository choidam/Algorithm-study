## 문제
- 프로그래머스 : 예산
- 서머코딩 / 윈터코딩 (~2018)
- https://programmers.co.kr/learn/courses/30/lessons/12982

<br/>

## 풀이
- 전형적인 그리디 알고리즘.
- 오름차순으로 정렬한 후 정해진 예산을 넘어가지 않을 때까지 sum에 더했다. 너무 간단한 문제❗️


<br/>

## 코드 

```c++

#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

int solution(vector<int> d, int budget) {
    int answer = 0;
    int sum = 0;
    sort(d.begin(), d.end()); // 오름차순으로 정렬
    
    for(int i=0; i<d.size(); i++){
        sum += d[i];
        
        if(sum<=budget){
            answer++;
        } else {
            break;
        }
    }
    return answer;
}

```


<br/>


## screenshot

![screenshot](./screenshots/prog_예산.png)


<br/>
