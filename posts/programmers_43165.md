## 문제
- 프로그래머스 : 타겟 넘버
- 깊이/너비 우선 탐색 (DFS/BFS)
- https://programmers.co.kr/learn/courses/30/lessons/43165

<br/>

## 풀이
- numbers 의 index 0 부터 탐색한다.
- 각각 index 값을 더하고 빼보면서 끝까지 탐색한다.
- numbers 의 끝까지 탐색을 완료하면 최종 sum 값과 target 값이 같은지 확인한다.
- 같다면 answer 값을 올려주고 아니면 return 하여 다시 탐색을 시작한다.
- 그동안 탐색은 항상 queue 에 넣고 시작했는데 vector 를 이용한 탐색은 처음이었다..


<br/>


## 코드

```c++
#include <vector>

using namespace std;
int answer = 0;

void dfs(vector<int> numbers, int target, int sum, int idx){
    if(idx >= numbers.size()){
        if(sum==target) answer++;
        return;
    }
    dfs(numbers, target, sum+numbers[idx], idx+1);
    dfs(numbers, target, sum-numbers[idx], idx+1);
}

int solution(vector<int> numbers, int target) {
    dfs(numbers, target, 0, 0);
    return answer;
}
```



<br/>

## screenshot

<img src="./screenshots/prog_타겟넘버.png" width="600" height="280">


<br/>
