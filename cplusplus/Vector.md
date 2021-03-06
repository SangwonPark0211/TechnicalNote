# **Vector**

## 작성자
[![tdm1223](https://avatars1.githubusercontent.com/u/21440957?s=100&v=4)](https://github.com/tdm1223)

## Vector
```cpp
#include<vector>
std::vector<int> v;
```
### 특징
- 배열과 유사하다. 배열의 크기는 고정이지만, vector의 크기는 동적으로 변한다는 차이점을 가진다.
- 개체들을 연속적인 메모리 공간에 저장한다.
    -  iterator 뿐 아니라 position index([])로도 접근이 가능
- 중간에 데이터 삽입, 삭제가 용이하지 않다. 
- 데이터를 순차적으로 저장한다. (검색 속도가 느리다, 랜덤 접근이 용이하다.)

### Vector를 사용해야 하는 경우
- 중간의 데이터 삽입이나 삭제가 없을 경우
- 순차적으로 저장된 데이터를 빈번하게 검색하지 않을 경우
- 특정 데이터가 저장된 위치를 파악하여 랜덤 접근 할 경우 ex) v[5]

### 장점 	
- 컨테이너의 끝에 원소 삽입 / 삭제가 빠르다.
- 개별 원소를 position index로 접근 가능(v[5]) O(1)
- 어떠한 순서로도 원소들을 순회할 수 있다. 
    - Random access iterating이 가능하다.
- 일반적으로 vector는 deque, list에 비해 원소에 대한 접근 속도와 컨테이너의 끝에서 삽입 / 삭제하는 속도가 가장 빠르다. 

### 단점 
- 맨 끝이 아닌 임의의 다른 위치에서의 삽입 삭제는 느리다.(선형시간)

### 사용시 주의 할점
- 확장시 재할당 비용이 크다.
- 요소를 추가하거나 제거하면 iterator가 무효화된다.

### push_back vs emplace_back
#### push_back
- push_back의 인자로서 필요한 객체를 생성 후 push_back 함수 내부에서 다시 한 번 복사가 일어난다.
- push_back을 빠져나갈 때 인자들이 파괴 된 후 해당 객체가 파괴된다. 
- vector에 객체 하나를 추가하는 과정에서 객체를 두 번 복사하고 삭제한다.
#### emplace_back
- 생성자로 넘길 인자만 넘겨주면 컴파일러는 알아서 생성자중에 해당 객체를 받을 수 있는 생성자를 찾아서 내부에서 생성시켜준다. 
- 객체 복제와 이동도 필요 없이 함수 내부에서 객체를 생성하여 삽입한다.
- 생성자 소멸자를 한 번씩만 호출한다.

### 사용팁
```cpp
vector<int> v; // int형 변수를 담는 비어있는 vector 생성
vector<pair<int,int>> v; // pair를 담는 비어있는 vector 생성
```
- 컨테이너이다 보니 pair, tuple도 담을 수 있다.
- 알고리즘 문제 풀이시 이를 활용하여 편하게 좌표(pair -> 2차원, tuple -> 3차원)를 표현할 수 있다.
