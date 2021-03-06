---
layout: post
title:  "R Markdown HTML Format"
date:   2018-06-01 03:13:04
categories: [R]
tags: [R, markdown]
---


# Intro

R Markdown으로 여러 포맷(md, html, pdf)을 만들 수 있고, 이 포맷 중 HTML 변환을 이용하면서 유용한 옵션 정보들을 살펴보려고 한다.

[R Studio Markdown Doc](https://rmarkdown.rstudio.com/index.html)  

[HTML Format Doc](https://rmarkdown.rstudio.com/html_document_format.html)

**Basic**
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
<br>


# TOC

<br>
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

<br>
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
<br>
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
<br>

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
<br>

# Hide Code  

코드 숨기기 기능
```
---
output:
  html_document:
    code_folding : hide
---
```
<br>
# Theme

Doc 참고를 해보면 쓸 수 있는 theme은 아래 인용 참조  
> theme specifies the Bootstrap theme to use for the page (themes are drawn from the Bootswatch theme library). Valid themes include "default", "cerulean", "journal", "flatly", "readable", "spacelab", "united", "cosmo", "lumen", "paper", "sandstone", "simplex", and "yeti". Pass null for no theme (in this case you can use the css parameter to add your own styles).

```
---
output:
  html_document:
    theme: cosmo
---
```

<br>
# Highlight

사용 가능 옵션은 아래 인용문 참조
> highlight specifies the syntax highlighting style. Supported styles include "default", "tango", "pygments", "kate", "monochrome", "espresso", "zenburn", "haddock", and "textmate". Pass null to prevent syntax highlighting.

```
---
output:
  html_document:
    theme: cosmo
    highlight : espresso
---
```
<br>

# Tabbed Sections

하위 목차를 탭 형식으로 표시해주는 옵션

```
## Quarterly Results {.tabset}

### By Product

(tab content)

### By Region

(tab content)
```
![](/images/2018.06/tab_section.png)  
위 이미지처럼 탭창으로 하위 목차를 구별 할 수 있게끔  
생성된다.  


### 추가 옵션  
```
## Quarterly Results {.tabset .tabset-fade .tabset-pills}

### By Product

(tab content)

### By Region

(tab content)
```
<br>


# R Chunk Options

```
{r,message=FALSE,warning=FALSE}
```
* message=FALSE
코드 실행 시 나오는 문구 생략  
예를 들어, 라이브러리 추가시 생성되는 메세지들 생략

* warning=FALSE
경고 문구 생략
