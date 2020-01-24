## 문제
- 프로그래머스 : 큰 수 만들기
- Greedy
- https://programmers.co.kr/learn/courses/30/lessons/42883

<br/>

## 풀이
- 너무 어려운 😭 그리디 알고리즘 😭😭
- ```bucket``` 에 조합하고자 하는 배열을 저장하고 ```removeAt``` 에 제거하는 배열을 저장한다.


<br/>


## 코드

```c++
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>

using namespace std;

string solution(string number, int k){
    vector<char> bucket; // 조합하고자 하는 배열
    vector<int> removeAt; // 제거하는 배열
   
    // 주어진 숫자로부터 하나씩 꺼내 모으면서, 모아둔 것 중 지금 등장한 것보다 작은 것들을 빼낸다
    for(const auto letter: number){
        // 현재 조합하고자 하는 배열이 비어있는 경우
        if(bucket.empty()){
            bucket.push_back(letter);
            continue;
        }
        // 현재 숫자들이 추가 될 숫자보다 작은 경우 -> 제거
        while(!bucket.empty() && removeAt.size()!=k && bucket.back()<letter){
            removeAt.push_back(bucket.back());
            bucket.pop_back();
        }
        bucket.push_back(letter);
    }
    
    string answer = removeAt.empty() ? number.substr(0, number.size()-k) : string(bucket.begin(), bucket.end());
    return answer;
}

```



<br/>

## screenshot

<img src="./screenshots/prog_큰수만들기.png" width="600" height="280">


<br/>
