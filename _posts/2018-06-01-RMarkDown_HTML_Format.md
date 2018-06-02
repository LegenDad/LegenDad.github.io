---
layout: post
title:  "R Markdown HTML Format"
date:   2018-06-01 03:13:04
categories: [R]
tags: [R, markdown]
---

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

# Intro
R Markdown으로 여러 포맷(md, html, pdf)을 만들 수 있고, 이 포맷 중 HTML 변환을 이용하면서 유용한 옵션 정보들을 살펴보려고 한다.

[R Studio Markdown Doc](https://rmarkdown.rstudio.com/index.html)  

[HTML Format Doc](https://rmarkdown.rstudio.com/html_document_format.html)

Basic
```
---
title : "EDA AvIto"
author : "LegenDad"
date : "2018년 6월 1일"
output : html_document
---
```
기본은 위와 같고,  
여기서 html_document에 옵션 주는 것을 활용해보자.


# TOC

Table Of Contents

목차 만들기 옵션으로 생각하면 된다.

## Basic

```
---
output :
  html_document:
    toc : true
---
```
위 옵션만으로 목차가 문서 맨 위에 자동으로 생성된다.


## Float

```
---
output :
  html_document:
    toc : true
    toc_float : true
---
```
생성된 목차를 사이드에 위치 시켜서,  
문서가 아래로 내려가도 목차를 계속 바로 확인 할 수 있게 하는 옵션  

![](/images/2018.06/toc_float.png)  

이미지 왼쪽이 toc만 추가,  
이미지 오른쪽이 toc_float 추가  

toc_float의 경우 기본 설정이  
하위 목차를 자동으로 숨김으로 되어 있어서  
위 이미지처럼 하위 목차 한 번에 다 표시 할려면  
옵션을 하나 더 추가해야 한다.

```
---
output:
  html_document:
    toc: true  
    toc_float:  
      collapsed: false
---
```

## Number

목차에 숫자 옵션 주는 기능  
number_sections
```
---
output:
  html_document:
    toc: true  
    toc_float:  
      collapsed: false
    number_sections : true
---
```

# Figure

기본값은 7x5로 설정되어 있어서  
변경 (10x4.5)할려면 아래와 같이 설정해 주면 된다.
```
---
output:
  html_document:
    fig_width: 10
    fig_height: 4.5
---
```

# Hide Code  

코드 숨기기 기능
```
---
output:
  html_document:
    code_folding : hide
---
```
