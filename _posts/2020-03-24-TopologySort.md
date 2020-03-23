---
title:  "위상 정렬"
excerpt: "Topology Sort"
categories:
  - algorithm
tags:
  - topology
  - sort
  - algorithm
last_modified_at: 2020-03-24T08:00:00-00:00
sitemap :
    changefreq : daily
    priority : 1.0
toc: true
---

## TopologySort(위상정렬)
### TopologySort란?
- 순서가 정해져있는 작업을 수행해야 할 때 그 순서를 정하기 위해 사용하는 정렬 알고리즘이다.
- DAG(Directed Acyclic Graph : 사이클이 없는 방향 그래프)에만 적용이 가능하다.
- 정렬의 결과는 여러가지가 나올 수 있다.

### TopologySort의 시간 복잡도
- 시간 복잡도 : `O(V+E)` (정점의 개수 + 간선의 개수)

### TopologySort의 구현
1. **진입차수가 0**인 정점을 큐에 삽입한다.
2. 큐에서 원소를 꺼내 연결된 **모든 간선을 제거**한다.
3. 간선 제거 후에 **진입차수**(특정한 노드가 있을때 그 노드로 들어오는 다른 노드의 개수)가 0이 된 정점을 큐에 삽입한다.
4. 큐가 빌 때까지 2~3의 과정을 반복한다.

- 모든 원소를 방문하기 전에 큐가 비었다면 사이클이 존재하는 것이다.
- 모든 원소를 방문하고 큐가 비었다면 큐에서 꺼낸 순서가 정렬의 결과가 된다.

### 소스코드
```cpp
#include<vector>
#include<queue>

using namespace std;

vector<int> result;
// 인자 : 간선 모음, 진입차수 배열, 크기
void topologySort(vector<vector<int>>& a, vector<int>& inDegree, int size)
{
    queue<int> q;
    // 진입 차수가 0인 노드를 큐에 삽입
    for (int i = 0; i < size; i++)
    {
        if (inDegree[i] == 0)
        {
            q.push(i);
        }
    }
    // 모든 노드 반복
    for (int i = 0; i < size; i++)
    {
        // n개를 방문하기 전에 큐가 빈다면 사이클 발생
        if (q.empty())
        {
            return;
        }
        int front = q.front();
        q.pop();
        result.push_back(front);
        for (int i = 0; i < a[front].size(); i++)
        {
            int x = a[front][i];
            // 새롭게 진입차수가 0이 된 정점을 큐에 삽입
            if (--inDegree[x] == 0)
            {
                q.push(x);
            }
        }
    }
}
```