---
layout: single
classes: wide
categories: C++, 문자열 나누기
title:  "[C++] stringstream, getline을 사용한 문자열 분리"
author_profile: true
---

### 문자열 나누는 문제
1. 먼저 stringstream과 getline을 사용하기 위해 sstream을 include해야 한다.

```c
#include <sstream>
```

2. 공백으로 구분된 문자 나누기
- stringstream 함수는 공백과 \n을 제외한 문자열을 빼낸다.

```c
#include <iostream>
#include <sstream>

using namespace std;

int main() {
    string x, y, z, res;
    string s = "apple 123 banana";
    stringstream ss(s);
    while (ss >> res) {
        cout << res << endl;
    }
    return 0;
}
```

```
<실행 결과>
apple
123
banana

Process finished with exit code 0
```

- vector에 넣고 출력할 수도 있다.

```c
#include <iostream>
#include <sstream>
#include <vector>

using namespace std;

int main() {
    string x, y, z, res;
    string s = "apple 123 banana";
    vector<string> a;
    stringstream ss(s);
    while (ss >> res) {
        a.push_back(res);
    }
    int i;
    for (i = 0; i < a.size(); i++) {
        printf("%s\n", &a[i][0]);
    }
    return 0;
}
```

```
<실행 결과>
apple
123
banana

Process finished with exit code 0
```

3. 공백 이외의 문자로 구분되어 있을 때 나누기
- 콤마(,), 슬래쉬(/) 등 공백 이외의 문자로 문자열이 구분되어 있다면 getline()을 추가로 사용해 문자열을 분리할 수 있다.

```c
#include <iostream>
#include <sstream>
using namespace std;

int main() {
    string x, y, z, res;
    string s = "red,blue,yellow";
    stringstream ss(s);
    while (getline(ss, res, ',')) {
        cout << res << endl;
    }
    return 0;
}
```

```
<실행 결과>
red
blue
yellow

Process finished with exit code 0
```
