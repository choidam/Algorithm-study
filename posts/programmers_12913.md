## 문제
- 프로그래머스 : 땅따먹기
- https://programmers.co.kr/learn/courses/30/lessons/12913
- DP


<br/>


## 풀이
```c++
#include <iostream>
#include <vector>
using namespace std;

int solution(vector<vector<int> > land)
{
   int answer = 0;
    int idx = 0, tmpmax, tmpidx;
    
    for(int i=0; i<land.size(); i++){ // 각 행 순회 : i
        tmpmax = 0;
        for(int j=0; j<4; j++){ // 각 열 순회 : j
            if(i==0){ // 첫 행 순회
                if(land[i][j] > tmpmax){
                    tmpmax = land[i][j];
                    tmpidx = j;
                    idx = j;
                }
            } else{ // 첫 행 순회가 아님 -> 조건 추가
                if(idx != j && land[i][j] > tmpmax){
                    tmpmax = land[i][j];
                    tmpidx = j;
                }
            }
        }
        
        tmpidx = idx;
        answer += tmpmax;
    }

    return answer;
}
```
- 간단하게 각 행에 대해 최댓값을 구하면서 했더니 테스트 케이스에선 오류가 없으나 제출하면 오류100%였다 🤬🤬


<br/>

```
1      2 3 5
5      6 7 8
4      3 2 1
1000   0 9 8
```
- 위 경우에 내가 만든 알고리즘을 대입하면 5+5+4+9 = 19 가 답이 된다.
- 사실 답은 1000을 고려한 5+7+3+1000 = 1013 이어야 한다. (그래서 DP인 것 같다..)

<br/><br/>

문제의 핵심은 🌟 열은 4개로 고정 🌟 이다. <br/>
그러므로 다음과 같은 과정을 반복한다. <br/>

1. 다음 칸 첫번째 열을 선택할 경우 이전의 2, 3, 4 열의 최대를 선택해야 한다.
2. 다음 칸 두번째 열을 선택할 경우 이전의 1, 3, 4 열의 최대를 선택해야 한다.
3. 다음 칸 세번째 열을 선택할 경우 이전의 1, 2, 4 열의 최대를 선택해야 한다.
4. 다음 칸 네번째 열을 선택할 경우 이전의 1, 2, 3 열의 최대를 선택해야 한다.


<br/> 

## 풀이2

```c++
#include <iostream>
#include <vector>
using namespace std;

int getmax(vector<int> v){
    int max = 0;
    for(int i=0; i<v.size(); i++){
        if(max < v[i]){
            max = v[i];
        }
    }
    return max;
}

int solution(vector<vector<int> > land)
{
   int answer = 0;
    
    for (int i = 0; i < land.size()-1; i++) {
        land[i+1][0] += getmax({land[i][1], land[i][2], land[i][3]});
        land[i+1][1] += getmax({land[i][0], land[i][2], land[i][3]});
        land[i+1][2] += getmax({land[i][0], land[i][1], land[i][3]});
        land[i+1][3] += getmax({land[i][0], land[i][1], land[i][2]});
    }
    answer = getmax(land[land.size()-1]);
    
    return answer;
}
```

<br/>

```
1      2 3 5
5      6 7 8
4      3 2 1
1000   0 9 8
```
<br/>

위 경우에 새로 만든 알고리즘을 대입하면

```
1      2    3    5
10     11   12   11
16     15   13   13
1015   16   25   34
```

이므로 답은 1015 가 무사히 나온다.

 ![screenshot](./screenshots/prog_땅따먹기.png)
 
 - 결과 성공 〰️‼️
 
 
 
 <br/>
 
 
 
 
 ## 반성
 - 쉬운 문제도 다시 보자 ,, 😔
 
