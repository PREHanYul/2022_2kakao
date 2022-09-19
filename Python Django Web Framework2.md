# Python Django Web Framework-2



###### (1)파이썬 설치

파이썬 설치 -> https://www.python.org/downloads/

파이썬 설치 완료

<img src="C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20220919235023908.png" alt="image-20220919235023908" style="zoom:25%;" />

파이썬 사용

<img src="C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20220919235210343.png" alt="image-20220919235210343"  />

![image-20220919235302163](C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20220919235302163.png)

잘 실행된다.



###### (2) Django 설치

음... 잘모르겠는데요...

py -m pip install django 치고

성공적으로 설치했다는 표시 받기.

![image-20220920000219318](C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20220920000219318.png)



django-admin 사용할 수 있는 명령어 확인하기.



###### (3)장고 프로젝트 생성하기

![image-20220920000656149](C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20220920000656149.png)

.은 현재 위치에 생성



결과

![image-20220920000808978](C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20220920000808978.png)

생성되었다.

###### (4) 장고 파일 생성시 생기는 파일들에 대해서

![image-20220920000924359](C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20220920000924359.png) -settings파일 중요하고 암튼 그렇다고함...

-urls  사용자가 접속하는 패스에 따라서 어떻게 누가 처리해줄 건가를 라우팅을 해주는 아주 중요한 파일...?

![image-20220920001219322](C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20220920001219322.png)

-manage 파일은 프로젝트 밖에 생기는데

여러가지 기능 들어간 유틸리티 파일이다.



###### (5) 장고 실행해보기



![image-20220920001515677](C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20220920001515677.png)



py manage.py라고 치면 여러 가지 명령어가 나온다.

여기서 필요한 건 

[staticfiles]밑에 있는 runserver.



![image-20220920001720932](C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20220920001720932.png)



###### (6)성공적으로 설치 결과

![image-20220920001820200](C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20220920001820200.png)



###### (7) 서버 중단과 포트번호 임의로 만들기

서버를 끄고 싶으면 crtl+c 누르기

만약에 서버를 이미 쓰고 있고 다른 서버로 만들려면

py manage.py  runserver 숫자정해주기 하면 된다.

