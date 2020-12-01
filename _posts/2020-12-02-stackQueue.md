---
title:  "스택으로 큐 구현하기 / 큐로 스택 구현하기"
excerpt: "스택과 큐"
categories:
  - algorithm
tags:
  - stack
  - queue
last_modified_at: 2020-12-02T08:00:50-00:00
sitemap :
    changefreq : daily
    priority : 1.0
toc: true
---

## 스택과 큐의 상호 구현
- 면접 보면서 정말 많이 받은 질문 중 하나이다.
- 처음 질문받았을 때 어버버 하면서 아무것도 대답 못했던 기억이 있고 두 번째 받았을 땐 자신 있게 작성하다 틀린 기억이 있는 부끄러운 기억이 있다.

## 스택으로 큐 구현하기
이론은 간단하다. 2개의 스택을 이용해서 구현하면 된다.
![1](/img/stackQueue.png)

1. Enqueue(삽입)
- 그냥 첫 번째 스택인 a에 추가만 하면 된다.

2. Dequeue(제거)
- 두 번째 스택인 b가 비어있지 않다면 b에 있는 값을 제거(반환) 하면 된다.
- 두 번째 스택인 b가 비었다면 첫 번째 스택인 a가 빌 때까지 a를 pop(제거)하면서 두 번째 스택인 b에 push(추가) 한다.

```cpp
class StackQueue
{
public:
	stack<int> a;
	stack<int> b;
	void Enqueue(int data)
	{
		a.push(data);
	}
	int Dequeue()
	{
		if (b.empty())
		{
			while (!a.empty())
			{
				b.push(a.top());
				a.pop();
			}
		}
		int data = b.top();
		b.pop();
		return data;
	}
};

```


## 큐로 스택 구현하기
- 큐로 스택을 구현하는 경우에도 큐 2개를 이용하면 스택을 구현할 수 있다.

```cpp
#include<queue>
using namespace std;
class QueueStack
{
public:
	queue<int> a;
	queue<int> b;
	void Push(int data)
	{
		if (a.empty())
		{
			a.push(data);
		}
		else
		{
			while (!a.empty())
			{
				b.push(a.front());
				a.pop();
			}
			a.push(data);
			while (!b.empty())
			{
				a.push(b.front());
				b.pop();
			}
		}
	}
	int Pop()
	{
		int data = a.front();
		a.pop();
		return data;
	}
};
```