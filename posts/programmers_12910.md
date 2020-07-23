## 문제
- 프로그래머스 : 나누어 떨어지는 숫자 배열
- https://programmers.co.kr/learn/courses/30/lessons/12910

<br/>

## 풀이
- 풀이를 적기도 민망한,,ㅎㅎ 정렬후 조건에 맞는 원소를 vector에 넣어주었다.

<br/> 

## 풀이

```c++
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

vector<int> solution(vector<int> arr, int divisor) {
    vector<int> answer;
    
    sort(arr.begin(), arr.end()); // 오름차순 정렬
    
    for(int i=0; i<arr.size(); i++){
        if(arr[i]%divisor == 0){
            answer.push_back(arr[i]);
        }
    }
    
    if(answer.size() == 0){
        answer.push_back(-1);
    }
    
    return answer;
}
```

<br/>

## screenshot

 <img src="./screenshots/prog_숫자배열.png" width="400"> 
