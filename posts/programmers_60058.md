## 문제
- 2020 kakao blind recruiment : 문자열 압축
- https://programmers.co.kr/learn/courses/30/lessons/60058

<br/>

## 코드
```c++
#include <string>
#include <vector>

using namespace std;

// 올바른 괄호 문자열
bool isRight(string s){
    int sum = 0;
    for (int i = 0; i < s.length(); i++) {
        if (s.at(i) == '(')
            sum++;
        else if (s.at(i) == ')')
            sum--;
        if (sum < 0)
            return false;
    }
    return true;
}

string solve(string s){
    if (s == "")
        return "";
    string u; string v;
    int i = 0;
    int left = 0; int right = 0;
    for (i = 0; i < s.length(); i++) {
        if (s.at(i) == '(')
            left++;
        else if (s.at(i) == ')')
            right++;
        if (left == right) {
            u = s.substr(0, i + 1);
            v = s.substr(i + 1);
            break;
        }
    }
    if (isRight(u))
        return u + solve(v);
    else {
        string temp = "(" + solve(v) + ")";
        u = u.substr(1, u.length() - 2);
        for (int i = 0; i < u.length(); i++) {
            if (u.at(i) == '(')
                temp = temp + ')';
            else
                temp = temp + '(';
        }
        return temp;
    }
}

string solution(string p) { 
    return solve(p);
}
```


<br/>

## screenshot
<img src="./screenshots/prog_괄호변환" width="300">
