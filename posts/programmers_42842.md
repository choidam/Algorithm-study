## 문제
- 프로그래머스 : 카펫
- 완전탐색
- https://programmers.co.kr/learn/courses/30/lessons/42842

<br/>

## 풀이
- brown 과 red 를 더해 전체 격자의 갯수 sum을 구한 다음, sum의 공약수를 이용해 가능한 width, height를 구한다.
- brown 과 width*2 + height*2 -4 가 일치하는 순간 값을 answer 에 push 한다.


<br/>


## 코드

```c++
#include <vector>

using namespace std;

vector<int> solution(int brown, int red){
    vector<int> answer;
    int width, height; // 가로, 세로 (가로 >= 세로)
    int tmpsum;
    int sum = brown + red; // 전체 격자 갯수
    
    for(int i=1; i<=sum/2; i++){
        if(sum%i == 0){
            height = i;
            width = sum/height;
            tmpsum = width*2 + height*2 - 4;
            if(tmpsum == brown) {
                answer.push_back(width);
                answer.push_back(height);
                return answer;
            }
        }
    }
    
    return answer;
}


```



<br/>

## screenshot

<img src="./screenshots/prog_카펫.png" width="600" height="280">


<br/>
