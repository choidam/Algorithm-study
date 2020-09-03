## 문제
- 프로그래머스 2018 kakao blind recruiment : 방금 그 곡
- https://programmers.co.kr/learn/courses/30/lessons/17683

<br/>

## 풀이
- 오 쉽네~! 하고 풀다가 진짜 여기에 몇 시간을 쏟은 건지.. 막 스킬이 필요한 건 아닌데 엄청 오래 걸렸다.
- `splitChart()` : 매개변수로 받은 char 를 기준으로 문자열을 split
- `findMeodyCode()`: 멜로디 문자열을 split 한다. (#처리가 약간 까다롭다.)
- `searchMelody()` : 음악과 멜로디가 완벽하게 일치하는 구간이 있는지 판별한다.

<br/>

## 코드

```c++
#include <string>
#include <vector>

using namespace std;

vector<string> splitChar(string str, char ch){
    vector<string> v;
    int ind = 0;
    for(int i=0; i<str.length(); i++){
        if(str[i]==ch){
            v.push_back(str.substr(ind, i-ind));
            ind = i+1;
        }
    }
    v.push_back(str.substr(ind, str.size()-1));
    return v;
}

vector<string> findMelodyCode(string melody){
    vector<string> melodyCode;
     for(int j = 0; j < melody.size() - 1; j++){
        string code = "";
        code += melody[j];
        if(melody[j+1] == '#'){               
            code += melody[j+1];
            j++;
        }
        melodyCode.push_back(code);
    }
    if(melody[melody.size() - 1] != '#'){
        string code = "";
        code += melody[melody.size() - 1];
        melodyCode.push_back(code);  
    }
    return melodyCode;
}

bool searchMelody(vector<string> m, vector<string> melody){
    bool result = true;
    for(int i=0; i<melody.size(); i++){
        if(melody[i] != m[0]) continue;
        
        int k = i;
        for(int j=0; j<m.size(); j++){
            if(melody[k]!=m[j]){
                result = false;
                break;
            }
            k++;
        }
        if(result){
            return result;
        }
        result = true;
    }
    return false;
}

string solution(string m, vector<string> musicinfos) {
    string answer = "(None)";
    int currentTime = 0;
    
    for(int i=0; i<musicinfos.size(); i++){
        vector<string> musicinfo = splitChar(musicinfos[i], ',');
        vector<string> startTime = splitChar(musicinfo[0],':');
        vector<string> endTime = splitChar(musicinfo[1],':');
        int sumTime = (stoi(endTime[0])-stoi(startTime[0]))*60 + (stoi(endTime[1])-stoi(startTime[1]));
        if(currentTime > sumTime) continue;
        if(currentTime == sumTime){
            if(answer != ("(None)")) continue;
        }
        
        vector<string> melodyCode = findMelodyCode(musicinfo[3]);
        vector<string> melody;
        
        for(int j=0; j<sumTime; j++){
            int ind = j%melodyCode.size();
            melody.push_back(melodyCode[ind]);
        }
        
        if(searchMelody(findMelodyCode(m), melody)){
            answer = musicinfo[2];
            currentTime = sumTime;
        }
        
    }
    
    return answer;
}
```

<br/>

## screenshot

<p align="ceenter"><img src="./screenshots/prog_인형뽑기.png" width="500"></p>

