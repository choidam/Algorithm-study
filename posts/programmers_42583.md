## 문제
- 프로그래머스 : 다리를 지나는 트럭
- stack / queue
- https://programmers.co.kr/learn/courses/30/lessons/42583

<br/>

## 풀이
- `vector<pair<int,int>> truckbridge` 안에 **트럭 무게** 와 **남은 길이** 를 같이 저장하는 것이 핵심이다.
- `weightSum` 에는 다리 위 트럭들의 무게 총합을 저장한다.

다리 위 트럭(`truckbridge`) 과 현재 대기하고 있는 트럭 리스트 (`truck_weights`) 가 모두 빌 때까지 while문을 실행한다.      

이 때, 

1. 현재 다리 위 트럭들의 무게 총 합을 계산한다. (weightSum)
2. 무게 총 합을 통해 다리가 무게를 견딜 수 있는 경우에만 트럭 리스트에 있는 가장 앞 트럭( `truck_weights.front()`)을 출발시킨다.      
즉, 다리에 있는 트럭 리스트에 가장 앞 트럭을 추가하고, 대기 트럭에서 제외한다.
3. 다리에 있는 모든 트럭 리스트의 남은 거리를 감소시킨다. (시간이 지났으므로)
4. 이 때 다리 트럭 리스트의 가장 앞 트럭의 거리가 0인 경우 (다리를 다 지난 경우) 제외시킨다.

사실 벡터에서 선입선출구조를 사용할 일이 없었어서 `front()`, `begin()` 은 이번 문제에서 처음 썼다.  `erase()` 같은 경우도 메모리를 많이 할당해서 잘 사용하지 않았는데, 벡터에서 FIFO 구조를 이렇게 적극적으로 사용한다면 차라리 `queue` 로 구현하는게 더 나았을 것 같다,, 고쳐보려고 했으나 졸려서 내일 고치겠다 

<br/>

## 코드

```c++
#include <vector>

using namespace std;

int solution(int bridge_length, int weight, vector<int> truck_weights) {
    vector<pair<int,int>> truckbridge; // <트럭 무게, 남은 길이>
    int weightSum = 0; 
    int time = 0;
    
    // 다리 위 트럭과 대기 트럭이 모두 빌 때까지 무한루프
    while((truck_weights.size()>0) || (truckbridge.size()>0)){
        time++;
        weightSum = 0;
        
        // 다리 위 트럭들의 무게 계산
        for(int i=0; i<truckbridge.size(); i++){
            weightSum += truckbridge[i].first;
        }
        
        // 다리가 무게를 견딜 수 있는 경우 트럭 출발
        if((truck_weights.size()>0) && (weightSum+truck_weights.front() <= weight)){
            truckbridge.push_back(make_pair(truck_weights.front(), bridge_length)); // 다리에 트럭 추가
            truck_weights.erase(truck_weights.begin()); // 대기 트럭에서 지움
        }
        
        // 다리 위 트럭들의 남은 거리 감소
        for(int i=0; i<truckbridge.size(); i++){
            truckbridge[i].second--;
        }
        
        // 도착한 트럭 제외
        if((truckbridge.size()>0) && (truckbridge.front().second<=0)){
            truckbridge.erase(truckbridge.begin());
        }
    }
    
    return time+1;
}
```

<br/>

## screenshot

<img src="./screenshots/prog_다리트럭.png" width="500">

