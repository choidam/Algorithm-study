## 문제
- 프로그래머스 Summer/Winter Coding (~2018) : 소수 만들기
- https://programmers.co.kr/learn/courses/30/lessons/12977

<br/>

## 풀이
- 중복 조합을 어떻게 처리해야 하나 정말 많이 고민을 했던 문제..
- 이 문제는 **서로 다른 세 개의 숫자** 를 택하는 것이 핵심이다. 3중 for문으로 쉽게 풀린다.

```c++
    for(int i=0; i<size; i++)
        for(int j=i+1; j<size; j++)
            for(int k=j+1; k<size; k++)
```

중복을 허용하지 않으므로 for문 출발점을 각각 `0`, `i+1`, `j+1` 으로 두는 것이 핵심이다.

<br/>

## 코드

```c++
#include <vector>
#include <iostream>
using namespace std;

// 소수 판별
bool isPrime(int num){
    if(num==0 || num==1) return false;
    for(int i=2; i<num/2; i++){
        if(num%i==0) return false;
    }
    return true;
}

int solution(vector<int> nums) {
    int answer = 0;
    int size = nums.size();
    int sum = 0;
    
    for(int i=0; i<size; i++){
        for(int j=i+1; j<size; j++){
            for(int k=j+1; k<size; k++){
                sum = nums[i] + nums[j] + nums[k];
                if(isPrime(sum)) answer++;
                sum = 0;
            }
        }
    }

    return answer;
}
```

<br/>

## screenshot

<p align="center"><img src="./screenshots/prog_소수만들기.png" width="500"></p>
