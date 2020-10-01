## 문제
- 프로그래머스 : 여행경로
- DFS / BFS
- https://programmers.co.kr/learn/courses/30/lessons/43164

<br/>

## 풀이
- 쉽네~ 하고 시작했다가 진짜 오래걸린 .. ㅠㅠ 우선 문자열로 된 티켓의 방문 여부를 어떻게 구분할지 막막했다.
- 방문 여부는 먼저 티켓들을 오름차순으로 정리한 후 (알파벳 순으로 방문하므로) 그 인덱스 값에 따른 `visited` 로 판별했다.
- 각 티켓을 순회하며 출발지와 `tickets[i][0]` 이 일치하고, 아직 사용하지 않은 티켓인 경우 재귀호출을 통해 DFS 탐색을 진행했다.
- 다만 아직 왜 탐색을 진행한 후 다시 티켓 사용 여부를   `false` 로 두고, `tmp` 벡터는 왜 사용했는지 아직 정확히 이해 가지 않는다.. 근데 이건 모든 풀이를 봐도 이렇게 풀던데 백트래킹인가..? 어렵다 ㅜㅜ


<br/>

## 코드

```c++
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

int maxcnt = 0;

void dfs(string start, vector<vector<string>> &tickets, vector<bool> &visited, vector<string> &answer, vector<string> &tmp, int cnt){
    
    tmp.push_back(start); // 경로 저장
    
    if(maxcnt < cnt){
        maxcnt = cnt;
        answer = tmp;
    }
    
    // 탐색
    for(int i=0; i<tickets.size(); i++){
        if(start == tickets[i][0] && visited[i] == false){
            visited[i] = true;
            dfs(tickets[i][1], tickets, visited, answer, tmp, cnt+1);
            visited[i] = false;
        }
    }
    
    tmp.pop_back();
}

vector<string> solution(vector<vector<string>> tickets) {
    vector<string> answer, tmp;
    vector<bool> visited(tickets.size(), false);
    sort(tickets.begin(), tickets.end()); // 오름차순 정렬
    int cnt = 0 ;
    dfs("ICN", tickets, visited, answer, tmp, cnt);
    
    return answer;
}
```
<br/>

## Screenshot

<p align="center"><img src="./screenshots/prog_여행경로.png" width="500"></p>

