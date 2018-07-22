---
title: 알고리즘 분석
subtitle: 시간복잡도와 공간복잡도
catalog: true
tags:
  - Algorithm
catagories:
  - Algorithm
date: 2017-04-23 20:26:15
header-img:
---

## 들어가기에 앞서...

안녕하세요? JayB 입니다.

저번 시간에는 알고리즘이 무엇이고 프로그램을 개발 할 때 알고리즘의 중요성에 대해 다뤄봤습니다.

오늘은 알고리즘 문제를 풀다보면 복잡도가 조건으로 주어지는 문제들을 심심찮게 보게 되는데 시간복잡도와 공간복잡도는 무엇이고

어떻게 계산해야 되는지에 대해 정리해보려고 합니다.

이해도 잘 되지 않고 복잡해 보이기만 했던 복잡도 개념.

오늘 한번 파헤쳐 보겠습니다.

아래는 알고리즘 트레이닝 사이트에서 문제를 풀다보면 종종 확인할 수 있는 문구 입니다.

![시간 및 공간복잡도](https://user-images.githubusercontent.com/20435620/29495553-b53cf4f8-85fc-11e7-8cf0-a916e24af6ad.png)


## 일반적인 알고리즘 분석

> 알고리즘을 이루는 명령어들의 수행횟수를 계산

그럼, 명령어들의 수행횟수를 어떻게 계산하여 어떻게 효율성을 판단한다는걸까요?

## 알고리즘의 성능 및 효율성

오늘은 *알고리즘의 성능 및 효율성* 을 평가하는데 있어서 크게 2가지로 평가한다고 합니다.

* *시간복잡도*

* *공간복잡도*

네, 맞습니다.

시간복잡도는 말 그대로 시간과 관련되어 있습니다.

> 작성한 프로그램이 얼마나 빠르게 수행되는지.

공간복잡도는 말 그대로 공간과 관련되어 있구요.

> 작성한 프로그램이 얼마나 많은 메모리를 차지하는지.

가장 좋은 알고리즘은 당연히 가장 적은 시간이 걸리고 메모리 사용량은 낮아야 겠죠?

어떤 알고리즘을 짜느냐에 따라서 프로그램의 **속도가 빠르고 메모리가 적게듭니다.**

즉, 개발자의 역할이 중요하다는 겁니다.

요즘에는 하드웨어의 무궁한 발전으로 인해 **시간복잡도** 의 중요도가 훨씬 높아졌고

대부분 시간복잡도만으로 알고리즘의 효율성을 판단한다고 합니다.

그럼 시간복잡도에 대해서 알아보도록 합시다.

## 시간복잡도 (Time Complexity) 란?

시간복잡도는 위에서 간단하게 설명하였습니다.

> 알고리즘을 평가하는데에 있어 프로그램의 수행시간을 분석하여 결과를 도출해내는 겁니다. (CPU 사용량)

절대적인 실행 시간을 나타내는 것은 아니고 *명령어들의 연산이 몇번이나 실행됬는지를 숫자로 표시하는 겁니다.*

원래의 시간 복잡도는 알고리즘을 구성하는 명령어들이 몇번이나 실행됬는지 + 명령어의 실행시간을 곱한 합계를 의미했지만,

명령어의 실행시간은 컴퓨터의 하드웨어 혹은 프로그래밍 언어에 따라 편차가 크게 달라지기 때문에

명령어의 실행시간을 제외한 **명령어의 실행 횟수만을** 고려합니다.

그럼 이 시간복잡도를 어떻게 표기해야 될까요?

네, 알고리즘의 기초를 조금이라도 학교에서 공부하셨다면 익숙하실 겁니다.

저도 이 표기법에 대해 제대로된 개념이 잡히지 않아 이해하는데 힘들었답니다.

아래와 같이 총 3개의 점근적 표기법으로 표기를 할 수 있습니다.

여기서, 점근적이라는 의미는 *가장 큰 영향을 주는 항만 계산** 한다는 의미입니다.

---

* 최상의 경우 : *오메가 표기법 (Big-Ω Notation)*

* 최악의 경우 : *빅오 표기법 (Big-O Notation)*

* 평균의 경우 : *세타 표기법 (Big-θ Notation)*

---

그 중 빅오 표기법 (최악의 경우)이 알고리즘 분석에서 가장 널리 사용됩니다.

이제 간단한 예제를 볼까요?

아래와 같은 함수가 있다고 칩시다.

```
[예제 1]

public void function(int a, n)
{
     int i=0, j=0;                                    1
     for (i = 0 ; i < n-1 ; i++)                      n            (i =0일때부터 i=n-1일때까지 계속 실행됨)
         for(j=i+1; j<n ; j++)                     (n-1) * n       (가장 많이 수행되는 경우를 생각)
            if (a[i] == a[j]) a[j] = 0 ;           (n-1) * (n-1)
}
```

위 예제의 명령어 실행횟수를 모두 더하면 2n²-2n+2 이 됩니다.

2n²-2n+2 의 상수는 생략 (점근적 표기)하고 최고차항만 생각하면 --> O(n²) 으로 표기 할 수 있습니다.

따라서, 위 예제의 시간복잡도는 **O(n²)** 입니다.

또 다른 예제를 볼까요?

```
[예제 2]

public int function2(int a[], int size, int key)  {
   int i = 0;                                         1
   for (i = 0; i < size; i++)                      size + 1
       if(a[i] == key)                               size
       return i;                                      1
   return -1;                                         1
}
```

위 예제의 명령어 실행횟수를 모두 더하면 뭐가 될까요? **2size + 4** 입니다.

2size + 4 의 상수를 생략하고 최고차항만을 구한다면?

위 예제의 시간복잡도는 **O(N)** 입니다.

예제 1 과 예제 2 의 프로그램중 어떤게 더 성능이 좋은 프로그램일까요?

**O(n²)** 과 **O(N)** 중 당연 **O(N)** 이겠죠? (직접 숫자를 대입해보시면 이해하기 편합니다)

**아래는 실행시간이 빠른 순으로 정리 된 빅오 표기법입니다**

---

```
O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2ⁿ) < O(n!) < O(nⁿ)
```

* O(1) : 입력 자료의 수에 관계없이 일정한 실행 시간을 갖는 알고리즘 (상수형)

* O(log N) : 입력 자료의 크기가 N일경우 log2N 번만큼의 수행시간을 가진다. (로그형)

* O(N) : 입력 자료의 크기가 N일경우 N 번만큼의 수행시간을 가진다. (선형)

* O(N log N) : 입력 자료의 크기가 N일경우 N*(log2N) 번만큼의 수행시간을 가진다. (선형로그형)

* O(N2) : 입력 자료의 크기가 N일경우 N2 번만큼의 수행시간을 가진다. (2차형)

* O(N3) : 입력 자료의 크기가 N일경우 N3 번만큼의 수행시간을 가진다. (3차형)

* O(2n) : 입력 자료의 크기가 N일경우 2N 번만큼의 수행시간을 가진다. (지수형)

* O(n!) : 입력 자료의 크기가 N일경우 n*(n-1) * (n-2)... * 1(n!) 번만큼의 수행시간을 가진다.
          ex)외판원 문제(TSP)의 기본적인 해법(팩토리얼형)

---

이제 알고리즘의 효율성을 어떻게 판단하는지 얼추 감이 잡히셨나요?

## 포스팅을 마치며...

문제를 해결하려고 할 때마다 시간복잡도를 분석하는 습관들 을이면 좋은 개발자가 될 수 있습니다.

개발자에게 있어서 문제라는 것은 항상 정답만을 찾는게 아닙니다.

상황에 맞춰 어떤 방법으로 접근해야 되는지가 중요합니다.

좀 더 나은 방법은 없는지에 대한 끊임없는 고민.

그 고민들이 쌓이고 쌓여 전반적인 사회적 문제들을 해결해나가는 것이지요.

미래를 위한 시간과 노력. 언젠가는 빛을 볼거라 믿습니다.

다음 포스팅엔 이진탐색트리, 다양한 정렬 알고리즘, 기술면접에서 나온 문제들을 풀어나가도록 하겠습니다.