## 문제
- 프로그래머스 : 네트워크
- https://programmers.co.kr/learn/courses/30/lessons/43162

<br/>

## 풀이
- 정말 간단한 DFS 문제! 백준과 다르게 변수 초기화 문제가 있었지만 금방 풀 수 있었다.

<br/>

## 코드

```c++
#include <string>
#include <vector>

using namespace std;

vector<vector<int>> map;
vector<bool> visited;
int ans, num;

void dfs(int node){
    visited[node] = true; // 방문 표시
    // 탐색
    for(int i=0; i<num; i++){
        if(map[node][i]==1 && visited[i]==false){
            dfs(i);
        }
    }
}

int solution(int n, vector<vector<int>> computers) {
    // 전역변수 초기화
    map = computers; ans = 0; num = n;
    for(int i=0; i<n; i++){
        visited.push_back(false);
    }
    
    for(int i=0; i<n; i++){
        if(visited[i]==false){
            ans++;
            dfs(i);
        }
    }
    
    return ans;
}
```

<br/>

## screenshot

<p align="center"><img src="./screenshots/prog_네트워크.png" width="500"></p>


<br/>

### 추가

> 이건 그냥.. 나만 이렇게 전역변수 초기화 하나 궁금해서 찾아본 다른 사람의 풀이

```c++
#include <string>
#include <vector>

using namespace std;

void DFS(int point, vector<vector<int>>& computers, vector<bool>& visit, int n){
    visit[point] = true;
    for (int i = 0; i < n; i++) {
        if (!visit[i] && computers[point][i]) DFS(i, computers, visit, n);
    }
}

int solution(int n, vector<vector<int>> computers) {
    int answer = 0;
    vector<bool> visit(n, false);
    
    for (int i = 0; i < n; i++) {
        if (!visit[i]) {
            answer++;
            DFS(i, computers, visit, n);
        }
    }
    return answer;
}
```

> 출처 : [Kimn's Blog](https://rile1036.tistory.com/25)

훨씬 간결하다. 전역변수를 초기화 하는 방법 대신 포인터를 사용해 구현했다. 이런 방법이..❗️    
포인터 귀찮아서 하나도 사용 안 하는데 ㅠㅠ 사용하는 버릇을 들여야 겠다.
