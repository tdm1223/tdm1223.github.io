---
title:  "forEach, map, filter, reduce, every, some"
excerpt: "forEach, map, filter, reduce, every, some"
categories:
  - javascript
tags:
  - javascript
  - forEach
  - map
  - filter
  - reduce
  - every
  - some
last_modified_at: 2021-05-02T08:00:50-00:00
sitemap :
    changefreq : daily
    priority : 1.0
toc: true
---

## forEach 
- 배열의 각각 요소들에 대해 주어진 콜백 함수를 실행한다.
- 예외가 발생하지 않으면 중간에 반복을 종료할 수 없다.

### custom forEach 함수
- 예외처리는 따로 하지 않았다.

```js
function customForEach(data, callback) {
    for (let i = 0; i < data.length; i++) {
        // 반복문 돌면서 callback 함수 실행
        callback(data[i]);
    }
}
```

## map
- 배열의 각각 요소들에 대해 주어진 콜백 함수를 호출한 결과를 모아 새로운 배열을 반환한다.

### custom map 함수
- 예외처리는 따로 하지 않았다.

```js
function customMap(data, callback) {
    let ans = []
    for (let i = 0; i < data.length; i++) {
        // callback함수 적용후 배열에 추가
        ans.push(callback(data[i], i));
    }
    return ans;
}
```

## filter
- 배열의 요소들에 대해 주어진 콜백 함수의 테스트를 통과하는 모든 요소를 모아 새로운 배열로 반환한다.

### custom filter 함수
- 예외처리는 따로 하지 않았다.
```js
function customFilter(data, callback) {
    let ans = []
    for (let i = 0; i < data.length; i++) {
        // callback함수로 필터링후 배열에 추가
        if (callback(data[i])) {
            ans.push(data[i]);
        }
    }
    return ans;
}
```

- 위 3개의 메서드들은 원본 배열을 변경하지 않는다.
- `foreach`를 제외하고 `filter`와 `map`은 새로운 결과를 반환한다.

## reduce
- 배열의 각각 요소들에 대해 주어진 콜백 함수를 실행하고, 하나의 누적된 결과값을 반환한다.

### customReduce 함수
- 예외처리는 따로 하지 않았다.

```js
function customReduce(data, callback, acc, idx) {
    if (data.length !== idx) {
        acc = callback(acc, data[idx]);
        return customReduce(data, callback, acc, idx + 1);
    }
    else {
        return acc;
    }
}
```

## every, some
- `every`와 `some` 메서드는 배열을 순회하면서 배열의 값들이 특정 조건을 만족시키는지 검사하는 메서드로서 호출한 배열이 조건을 만족하는지, 만족하지 못하는지를 알려준다. 
- `every`는 배열의 모든 값이 조건을 만족해야 한다.
- `some` 은 일부만 만족해도 `true`를 반환 한다.


