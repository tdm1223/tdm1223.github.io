---
title:  "Jekyll 블로그 에러 해결"
excerpt: "Internal Error: Invalid UTF-8 에러 해결"
categories:
  - jekyll
tags:
  - jekyll
  - internal
  - utf-8
last_modified_at: 2020-03-15T08:18:50-00:00
sitemap :
    changefreq : daily
    priority : 1.0
toc: true
---

## 문제
- 컴퓨터 포멧 후 깃 블로그 환경을 다시 구축하던 도중 생겼던 문제다.
- 환경을 구축 후 `bundle exec jekyll serve` 명령어를 실행하는데 아래와 같은 에러가 났다.
![에러1](https://user-images.githubusercontent.com/21440957/76699493-45a7d580-66f1-11ea-9c2d-74889c371aa2.PNG)

## 해결
- 이것 저것 검색하며 해결해 보려했지만 잘 적용 되지 않았고 생각보다 간단한 문제였다.
- **레포지토리 경로**에 **한글**이 존재해서 저 명령어가 먹지 않았던 것이다.
- **레포지토리를** 옮기고 다시 `bundle exec jekyll serve` 명령어를 실행하니 제대로 적용된걸 확인할 수 있었다.
![해결](https://user-images.githubusercontent.com/21440957/76699531-a8996c80-66f1-11ea-87f8-f341f04ac09d.PNG)

