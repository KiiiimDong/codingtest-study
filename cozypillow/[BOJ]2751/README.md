# 2751. 수 정렬하기 2
### [문제](https://www.acmicpc.net/problem/2914)

N개의 수가 주어졌을 때, 이를 오름차순으로 정렬하는 프로그램을 작성하시오.

### 입력
첫째 줄에 수의 개수 N(1 ≤ N ≤ 1,000,000)이 주어진다. 둘째 줄부터 N개의 줄에는 수가 주어진다. 이 수는 절댓값이 1,000,000보다 작거나 같은 정수이다. 수는 중복되지 않는다.

```
# 입력 예시
5
5
4
3
2
1
```



### 출력
첫째 줄부터 N개의 줄에 오름차순으로 정렬한 결과를 한 줄에 하나씩 출력한다.

```
#출력 예시
1
2
3
4
5
```



### 풀이

```python
# 입력
import sys
input = sys.stdin.readline

N = int(input())

num_list = []
for i in range(N):
    num_list.append(int(input()))

# 정렬
num_list = sorted(num_list)


# 출력
for num in num_list:
    print(num)

```



---

### [**참고한 글 :: input과 sys.stdin.readline의 차이점**](https://xsop.tistory.com/40)



> #### 💡 속도가 중요한 문제, 특히 알고리즘 문제 같은 경우에서 sys.stdin.readline을 사용합니다.

백준 문제를 풀다보면 시간초과에 걸리는 경우가 많다. 대개 이런 경우에 구글링을 해 보면 위와 같은 글들과 마주하게 된다. 분명 다들 이걸 사용하면 좋다고는 하는데... 그 이유에 대해서 알려주는 사람이 좀체 보이지 않았다. 검색해도 납득이 될만한 설명이 잘 없어서 한 번 열심히 찾아봤다.



### sys 모듈이란?

> sys 모듈은 파이썬 인터프리터가 제공하는 변수와 함수를 직접 제어할 수 있게 해주는 모듈이다. 

이렇게만 말하는 너희들... 정말 나빴어... 나는 이런 말 들어도 알아들을 수 없다구...

이 글을 뚫어져라 쳐다보고, 곰곰히 생각해보면, 그래도 대충이나마 감이 올 것도 같다. 내 생각엔... 

파이썬이 제공하는 기본 함수들도 결국 하나의 함수다. 그 속을 뜯어보면 우리가 직접 함수를 만들어 정의해놓은 것처럼, 여러가지 변수들로 이루어져있을 것이다. 가령 input()함수의 경우 무언가 넣어줘야만 작동한다. 무언가 지정해줘야만 작동하는 값을 우리는 **하이퍼 파라미터**라고 부른다. 

이제 sys 모듈을 이용해 입력하는 법을 보면..

```python
sys.stdin.readline
```

sys 모듈 안에 있는 stdin(아마도 standard-input) 표준입력 기능의 .readline 한 줄 읽기... 가 아닐까?



다음으로는 input()과 sys.stdin.readline() 의 차이점에 대해 알아보자.





### 차이점

**① input은 먼저 입력받은 값을 살펴보고, 개행문자를 삭제시키는 작업을 수행한다.**

입력된 값에 줄바꿈이 있는지 없는지 확인하는 작업을 한 후, 만약 줄바꿈이 들어있으면 없앤다는 것이다. 원래 문자열에서 어떤 작업을 취했으니 1차로 속도가 느려진다.

하지만 **sys.stdin.readline은 개행 문자를 포함한 값을 그대로 받아온다.** 그러면 부차적인 작업이 필요한 input에 비해 속도가 늦어지지 않을 것이다. 그리고 **줄바꿈을 한 정보가 그대로** 필요할 때에도 유용하게 쓰인다. (다시 말해, apple을 쓰고 엔터를 입력하면, "apple\n" 이 입력된다.)



**② input은 매개변수로 문자열(String)을 Console에 출력한다.**

Console에 출력을 한다는 것은 문자열을 입력받는 일 외에 해야하는 일이 하나 더 있다는 것을 뜻한다. 이것 역시 속도가 늦어지는 이유가 되겠다. 하지만 Console에 꼭 출력을 해야할 때에는 input을 사용한다.



### 결론

![백준 채점](img.jpg)

아무튼.. 제한된 자원안에서 목적을 빨리 수행하는 능력을 기르는 게 알고리즘 테스트니까 sys.stdin.readline 사용을 습관화하자. 일반 input()을 사용한 것은 시간초과가 나왔지만, 그 다음 채점한 것은 아래 코드를 상위에 추가해준 것 뿐인데 시간초과가 나지 않았다.

 ```python
import sys
input = sys.stdin.readline
 ```

