# Python Django Web Framework-2



###### (1)파이썬 설치

파이썬 설치 -> https://www.python.org/downloads/

파이썬 설치 완료

![image](https://user-images.githubusercontent.com/108383234/191441459-e7ccd76a-631e-46b5-be70-dab414267c98.png)


파이썬 사용
![image](https://user-images.githubusercontent.com/108383234/191441510-4a31ee88-4a64-4ed6-a9a6-94a50902e301.png)

![image](https://user-images.githubusercontent.com/108383234/191441533-46426565-a59d-4125-84a4-5acbeb7aa455.png)

잘 실행된다.



###### (2) Django 설치

음... 잘모르겠는데요...

py -m pip install django 치고

성공적으로 설치했다는 표시 받기.

![image](https://user-images.githubusercontent.com/108383234/191441575-7fc51b50-7909-47f0-8f81-24212aba1a0b.png)



django-admin 사용할 수 있는 명령어 확인하기.



###### (3)장고 프로젝트 생성하기
![image](https://user-images.githubusercontent.com/108383234/191441607-ce527f65-83f5-4008-846c-a7f334274c83.png)

.은 현재 위치에 생성



결과
![image](https://user-images.githubusercontent.com/108383234/191441636-8eaa4cd7-4fb1-4b36-aefe-5464542b50e8.png)

생성되었다.

###### (4) 장고 파일 생성시 생기는 파일들에 대해서

![image](https://user-images.githubusercontent.com/108383234/191441696-9201695f-91ff-4735-b931-44d48b2ae6a8.png)
 -settings파일 중요하고 암튼 그렇다고함...

-urls  사용자가 접속하는 패스에 따라서 어떻게 누가 처리해줄 건가를 라우팅을 해주는 아주 중요한 파일...?

![image](https://user-images.githubusercontent.com/108383234/191441731-1d0980ee-3162-4995-b060-0a0ea5f40772.png)


-manage 파일은 프로젝트 밖에 생기는데

여러가지 기능 들어간 유틸리티 파일이다.



###### (5) 장고 실행해보기



![image](https://user-images.githubusercontent.com/108383234/191441761-25d54b3f-d4e5-4bfd-a22b-9ce7da66357f.png)




py manage.py라고 치면 여러 가지 명령어가 나온다.

여기서 필요한 건 

[staticfiles]밑에 있는 runserver.



![image](https://user-images.githubusercontent.com/108383234/191441802-a33032a0-0def-4281-9ef2-6e31d0011272.png)




![image](https://user-images.githubusercontent.com/108383234/191441844-4b8703f2-ca48-43b5-b127-a6cbc876bc3f.png)




###### (7) 서버 중단과 포트번호 임의로 만들기

서버를 끄고 싶으면 crtl+c 누르기

만약에 서버를 이미 쓰고 있고 다른 서버로 만들려면

py manage.py  runserver 숫자정해주기 하면 된다.

