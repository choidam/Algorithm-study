## 문제
- 프로그래머스 : 프린터
- https://programmers.co.kr/learn/courses/30/lessons/42587

<br/>

## 풀이
- 우선순위 Queue 를 이용하면 쉽게 풀 수 있는 문제 ❗️
- ``` queue<pair<int,int>> q ``` 에 문서의 index, value 를 저장한다.
- ``` priority_queue<int> pq ``` 는 문서의 value 에 따라 내림차순으로 자동으로 정렬한다. 즉, 가장 중요도가 높은 문서가 항상 ``` pq.front() ``` 에 있다.


<br/>


## 코드 

```c++

#include <queue>
#include <vector>

using namespace std;

int solution(vector<int> priorities, int location) {
    int answer = 0;
    
    queue<pair<int,int>> q;
    priority_queue<int> pq; // 우선순위 큐 - 숫자가 높은 순대로 정렬
    
    for(int i=0; i<priorities.size(); i++){
        q.push(make_pair(i, priorities[i]));
        pq.push(priorities[i]);
    }
    
    while(!q.empty()){
        int cur_index = q.front().first;
        int cur_value = q.front().second;
        q.pop();
        
        if(pq.top() == cur_value){ // 현재 문서가 가장 중요도가 높은 경우 (pq.top() 이 가장 중요도 높음)
            pq.pop();
            answer++;
            
            if(cur_index == location){
                return answer;
            }
        } else { // 현재 문서보다 중요한 문서가 있는 경우
            q.push(make_pair(cur_index, cur_value)); // 다시 q에 push
        }
        
    }
    
    return answer;
}

```


<br/>


## screenshot

<img src="./screenshots/prog_프린터.png" width="600" height="280">


<br/>
