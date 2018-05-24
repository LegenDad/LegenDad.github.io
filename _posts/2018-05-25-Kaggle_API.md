---
layout: post
title:  "Kaggle API"
date:   2018-05-25 01:05:04
categories: [kaggle]
tags: [kaggle]
---

# Installation
[Kaggle API GitHub](https://github.com/Kaggle/kaggle-api)
```
pip install Kaggle
```

# API credentials
```
kaggle --version
Unauthorized: you must download an API key from https://www.kaggle.com/<username>/account
Then put kaggle.json in the folder /home/jeon/.kaggle
```
Download json file on Kaggle Account Pages API  
And move json file to Kaggle Path  

```
pip show Kaggle
```


# LookUP

```
kaggle --help
```
* **competitions** : *Commands related to Kaggle competitions*
* **datasets**: *Commands related to Kaggle datasets*
* **config** : *Configuration settings*

```
kaggle competitions --help
kaggle datasets --help
kaggle config --help
```

help 옵션으로 필요 명령을 직관적으로 확인 가능하다.  

```
kaggel competitions --help

  list
  files
  download
  submit
  submissions
```


Submissions 파일 다운로드는 api로는 아직 지원하지 않는 듯 하다.  

API 사용의 장점은 웹을 통하지 않고,   
데이터셋 다운로드 및 submission 제출이 있겠지만...   
api를 사용한다고 속도가 빠르지는 않다.  
웹인터페이스를 이용하는 중간 과정을 생략하는 정도인 듯 하다.   
