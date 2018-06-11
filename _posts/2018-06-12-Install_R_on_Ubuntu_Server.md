---
layout: post
title:  "Install R on Ubuntu Server"
date:   2018-06-12 03:13:04
categories: [R]
tags: [R, ubuntu]
---

# Intro

* 우분투 서버에 R 설치 경험기
* 개인 서버가 아닌 기관 대여 서버라서 포트 사용 및 설치 제한 조건
* r studio 활용이 어려운 조건에서 설치 및 활용기

<br>

# Preparation

* [R Cran Info](https://cran.r-project.org/bin/linux/ubuntu/)  
리눅스 배포판 설치 매뉴얼  


* [Ubuntu CodeName](https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_%EC%A2%85%EB%A5%98_%ED%99%95%EC%9D%B8,_%EB%A6%AC%EB%88%85%EC%8A%A4_%EB%B2%84%EC%A0%84_%ED%99%95%EC%9D%B8)  
우분부 코드 네임 얻는 법
검색으로 위키에서도 확인 가능하나 서버에서 바로 확인하는 법

* [Cran Mirror URL](https://cran.r-project.org/mirrors.html)  
저장소 등록을 위해 쓰일 미러 사이트 주소 리스트

<br>

# Installation

### 우분투 코드 네임 확인
```bash
root@....:~# grep . /etc/*-release
/etc/lsb-release:DISTRIB_ID=Ubuntu
/etc/lsb-release:DISTRIB_RELEASE=14.04
/etc/lsb-release:DISTRIB_CODENAME=trusty
...
```
`grep . /etc/*-release` 입력하면 위와 같은 정보가 출력  
버전 정보와 코드 네임이 확인 가능하다.  
위 코드는  14.04버전에 코드네임 trusty  
16.04버전의 경우는 코드네임이 zesty이다.

### 미러 사이트 주소를 저장소 리스트에 등록

한국 미러 주소 중 `http://cran.biodisk.org/`을 사용할 예정

```
$ sudo echo "deb http://cran.biodisk.org/bin/linux/ubuntu/ trusty” | sudo tee -a /etc/apt/sources.list  
```

shell 명령어가 궁금하면  
https://explainshell.com
이 사이트에서 입력하면 잘 설명해준다.

위 명령어는 echo ""의 내용을 인풋해서  
아웃풋으로 sources.list파일에 추가해준다는 내용이다.


### 공개키 추가
```bash
gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9
gpg -a --export E084DAB9 | sudo apt-key add -
```

### Install R

```bash
$ sudo apt-get update        
$ sudo apt-get install r-base
```

### 에러 발생 상황

`apt-get update`에서 오류 발생으로  
저장소 업데이트가 되지 않는다면
`sources.list`파일 열어서  
trusty나 코드 네임 뒤에 `/`입력하고 진행

추가로 gpg error가 발생하면  
해당 gpg key 확인 후

```bash
gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9
gpg -a --export E084DAB9 | sudo apt-key add -
```
위 코드에서 key값 변경해서 진행 후,
다시 인스톨 명령 실행하면 된다.

`which R`이나 `R --version`으로 설치 확인

<br>

# devtools package

이래저래 활용이 많고 추후에 깔려면 귀찮으니
미리 설치
```R
install.packages("devtools")
```

설치가 되면 좋지만, 에러가 발생하는 경우가 있다.

이런 경우에는 터미널에서 의존성 패키지를 설치하고 재실행

```bash
sudo apt-get install libssl-dev
sudo apt-get install libcurl4-openssl-dev
```
<br>

# Jupyter Notebook 연결  

* R Studio Server를 활용하면 좋지만,
사용할 수 있는 포트 제한으로 해당 프로그램 사용 불가
* GUI 기능을 사용하기 위해서,
포트가 열려진 쥬피터 노트북 활용
* 포트 사용 문제로 아나콘다는 활용 불가
* 콘다에서는 r-essential 설치로 해결 했지만
위와 같은 서버 상황에서는 IRKernel 설치로 진행

[IRKernel](https://github.com/IRkernel/IRkernel)

> install.packages('devtools')
> devtools::install_github('IRkernel/IRkernel')  
> IRkernel::installspec()

> in R 3.3
> IRkernel::installspec(name = 'ir33', displayname = 'R 3.3')
> in R 3.2
> IRkernel::installspec(name = 'ir32', displayname = 'R 3.2')

devtools는 설치했고 3.4버전으로 설치했으니  

R에서
```R
devtools::install_github('IRkernel/IRkernel')
IRkernel::installspec(name = 'ir34', displayname = 'R 3.4')
```

여기까지 완료되서  
쥬피터 노트북 실행시키면
쥬티퍼 노트북에서도 R을 사용할 수 있게 된다.
