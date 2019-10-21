## 문제
- 프로그래머스 : K번째 수 
- https://programmers.co.kr/learn/courses/30/lessons/42748

<br/>

## 풀이 
- 벡터 값에 대해 차근차근히 접근하면 쉽게 풀 수 있다.
- Idx 값에 대해 1씩 빼주어야 한다.

<br/>

```c++
#include <algorithm>
#include <vector>

using namespace std;

vector<int> solution(vector<int> array, vector<vector<int>> commands) {
    vector<int> answer;
    
     for(int i=0; i<commands.size(); i++){
        vector<int> arr = commands.at(i);
        
        int firstIdx = arr.at(0);
        int lastIdx = arr.at(1);
        int ansIdx = arr.at(2);
        
        if(firstIdx == lastIdx){
            int ans = array.at(firstIdx-1);
            answer.push_back(ans);
        } else {
            vector<int> tmp;
            for(int i=firstIdx-1; i<=lastIdx-1; i++){
                tmp.push_back(array.at(i));
            }
            sort(tmp.begin(), tmp.end());
            answer.push_back(tmp.at(ansIdx-1));
        }
    }
    return answer;
}
```

<br/>

## screenshot

![screenshot](./screenshots/prog_k번째수.png)
