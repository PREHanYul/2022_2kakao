# Python Django Web Framework-3

### app만들기

###### (1) 알아야하는 지식

project 안에서 만드는 것이 아님.

app이라는 더 작은 단위에서 구현할 것.

app안에 view가 있고 view안에는 함수들이 있음

그것들로 구체적인 구현을 함.

DB도 직접 접근이 아니고 djando에서 제공하는

model이라는 것이 있는데 이걸 사용할 거임.



###### (2)그래서 어떤 부분을 할 것인지

사용자가 다양한 경로로 들어오면 이제 이걸 누구에게

임위할 것인지 urls.py을 수정하고 코딩하는 게 이번 시간 목표.



###### (3)Django Model

장고 내장 ORM

ORM은 SQL을 직접 작성하지 않아도 장고 모델을 통해서 

DB에 접근한다.



###### (4)app만들기

![](C:\Users\LG\Documents\제대 컴공 3학년 2학기\기초웹개발론\앱만들기.JPG)

djaogo -admin startapp [이름] 하면

![](C:\Users\LG\Documents\제대 컴공 3학년 2학기\기초웹개발론\앱폴더생성된거.JPG)

이렇게 파일이 생성된다.