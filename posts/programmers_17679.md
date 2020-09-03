## 문제
- 프로그래머스 2018 kakao blind recruiment : 프렌즈 4블록
- https://programmers.co.kr/learn/courses/30/lessons/17679

<br/>

## 풀이
-   `flag` 는 4블록이 터졌는지 여부를 판별한다. 4블록이 터지지 않기 시작하면 무한루프를 멈춘다.
- 처음에 4블록 터지는것, 중복 터지기 어떻게 판별해야 할 지 감이 안 잡혔는데, 굳이 queue, DFS, BFS 쓰지 않아도 if문으로 판별이 가능하다. 너무 어렵게 풀 생각만 했다..
- 터질 블록을 표시하고 마지막에 제거 후 아래로 떨어지게 하는 데에도 시간을 많이 쏟았다. 

<br/>

## 코드

```c++
#include <string>
#include <vector>

using namespace std;

int solution(int m, int n, vector<string> board) {
    int answer = 0;
    bool flag = false;
    
    while(flag==false){
        vector<vector<bool>> visit(m, vector<bool>(n));
        flag = true;
        for(int i=0; i<m-1; i++){
            for(int j=0; j<n-1; j++){
                // 이미 제거가 된 경우
                if(board[i][j]==0) continue;
                
                // 2x2 모두 같을 경우
                if((board[i][j]==board[i][j+1]) && (board[i][j]==board[i+1][j]) && (board[i][j]==board[i+1][j+1])){
                    // 방문 표시
                    visit[i][j] = true;
                    visit[i+1][j] = true;
                    visit[i][j+1] = true;
                    visit[i+1][j+1] = true;
                    flag = false;
                }
            }
        }
        
        // 제거하기
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if(visit[i][j]==true){
                    answer++;
                    for(int k=i-1; k>=0; k--){
                        board[k+1][j] = board[k][j];
                        board[k][j] = 0;
                    }
                }
            }
        }
    }
    return answer;
}
```

<br/>

## screenshot

<p align="center"><img src="./screenshots/prog_프렌즈4블록.png" width="500"></p>

