## 문제
- 프로그래머스 : 구명보트
- greedy
- https://programmers.co.kr/learn/courses/30/lessons/42885

<br/>

## 풀이
- 구명보트에 탈 수 있는 인원은 최대 2명이므로 가장 무게가 적게 나가는 사람과 가장 무게가 많이 나가는 사람이 타는 것이 가장 효율적이다.

1. 가장 가벼운 사람 + 무거운 사람 <= limit  : 한 보트에 두 명 탑승 가능
2. 가장 가벼운 사람 + 무거운 사람 > limit : 무거운 사람 혼자서 탑승 가능

-  `head` 와 `tail`  변수를 사용해 가장 가벼운 사람과 무거운 사람에 접근해 문제를 풀었다.

<br/> 

## 코드

```c++
#include <iostream>
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

int solution(vector<int> people, int limit) {
    int answer = 0;
    
    sort(people.begin(), people.end()); // 오름차순 정렬
    int head = 0; int tail = people.size() - 1;
    
    while(head<=tail){
        if(people[head]+people[tail] <= limit){
            head++;
            tail--;
        } else {
            tail--;
        }
        answer++;
    }
    
    return answer;
}
```

<br/>

## screenshot

 <img src="./screenshots/prog_구명보트.png" width="600"> 
