## 문제
- 프로그래머스 : 스킬트리
- 서머코딩 / 윈터코딩 (~2018)
- https://programmers.co.kr/learn/courses/30/lessons/49993

<br/>

## 풀이
- 처음에 완전 탐색인가 싶었는데,, hash map 을 사용하면 쉽게 풀 수 있다❗️
- hash map 에 스킬 순서를 저장한 후, skill_trees 를 순회하며 각 값을 비교한다.
- 진짜 엄청 삽질했다 .. map 사용할 생각도 못했다 .. 반성 😔


<br/>


## 코드

```c++
#include <map>
#include <vector>

using namespace std;

int solution(string skill, vector<string> skill_trees){
    int answer = 0;
    
    map<char, int> tree;
    
    // hash map 에 스킬 순서를 저장 (default = 0)
    for(int i=0; i<skill.length(); i++){
        tree[skill[i]] = i+1;
    }
    
    // skill tree 순회
    for(auto skt: skill_trees){
        int count = 1;
        bool check = true;
        
        for(int i=0; i<skt.length(); i++){
            
            // 스킬 순서가 맞지 않다면 탈출
            if(tree[skt[i]] > count){
                check = false;
                break;
            
            // 최소 스킬 트리를 익혔다면 다음 스킬을 익힐 수 있도록 증가시킴
            } else if (tree[skt[i]] == count ){
                count++;
            }
        }
        
        // 모두 이상 없이 통과했을 경우 -> 모든 스킬 배울 수 있음
        if(check){
            answer++;
        }
    }
    
    return answer;
}
```



<br/>

## screenshot

<img src="./screenshots/prog_스킬트리.png" width="600" height="280">


<br/>
