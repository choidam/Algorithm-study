## 문제
- 프로그래머스 : 다트 게임
- 2018 kakao blind recruiment [1차]
- https://programmers.co.kr/learn/courses/30/lessons/17682


<br/>

## 풀이

- 처음엔 숫자와 결과값을 일일이 변수에 저장했는데 역시나 메모리 오류가 발생했다.
- 문자열에 입력된 숫자/보너스/옵션을 가리키는 cnt 변수, 몇 번째 숫자를 계산하는지 가리키는 idx 변수를 활용하자 ,,!

<br/>


## 코드 

```c++
#include <string>

using namespace std;

int solution(string dartResult) {
     int answer = 0;
    
    int nArr[3] { 0 }; // 숫자와 계산 결과를 저장
    int cnt = 0; // 숫자 - 보너스 - 옵션 문자열 순서 저장
    int idx = 0; // 세 문자열의 순서 저장
    int leng = dartResult.length();
    
    for(int i=0; i<leng; i++){
        if(cnt == 0){
            int n = dartResult[i] - 48;
            nArr[idx] = n;
            
        } else if (cnt == 1){ // 보너스 점수 계산 - S, D, T
            if(dartResult[i] == '0'){
                nArr[idx] *= 10;
                cnt--;
            } else if (dartResult[i]=='D'){
                int n = nArr[idx];
                nArr[idx] = n*n;
            } else if (dartResult[i]=='T'){
                int n = nArr[idx];
                nArr[idx] = n * n * n;
            }
        } else { // 옵션 점수 계산 - *, #
            if(dartResult[i] == '*'){
                nArr[idx] *= 2;
                if(idx-1 >= 0){
                    nArr[idx-1] *= 2;
                }
            } else if (dartResult[i] == '#'){
                nArr[idx] *= -1;
            } else {
                i--;
            }
            idx++;
        }
        cnt++;
        cnt = cnt % 3;
    }
    
    for(int i=0; i<3; i++){
        answer += nArr[i];
    }
    
    return answer;
}

```


<br/>


## screenshot

![screenshot](./screenshots/prog_다트게임.png)


<br/>
