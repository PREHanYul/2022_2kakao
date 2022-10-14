### 1) 스크립트 변수 선언

#### 스크립트의 루트에서 선언한 public 변수

​	inspector에 나타남

#### 함수 내에서 선언한 변수

​	지역변수:인스펙터에 나타나지 않음

private 선언된 변수도 인스펙터에 나타나지 않음.

#### 유니티의 이름 선언 규칙

​	변수: 소문자로 시작

​	함수 및 클래스 :대문자로 시가

​	단어가 바뀔 때마다 대문자

-여기 부분 어디를 설명하는 건지 수업을 안들어서 모르겠넹...;;



### 2) 디버그 로그 작성

프로그램 실행 시 디버그 및 다양한 메세지 출력할 수 있다.

Conscle에서 확인

#### 옵션

##### Clear on Play

 : 실행 시 콘솔창을 지우고 다시 기록 

##### Error Pause

: 에러가 나면 멈춤

##### Collapse 

: 같은 종류의 에러를 하나로 표시



###### 적용 예

![image-20221012183342798](C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20221012183342798.png)

물체가 땅에 닿을 때 소리는 나는 debuglog



### 3) 키보드와 마우스로 입력 받기

#### 유니티 입력 시스템

[Edit]->[Project Settings]->[Input]



##### 마우스 버튼

mouse 0: 왼쪽 버튼

mouse 1: 오른쪽 버튼

mouse 2: 가운데 버튼



##### 키 입력 처리

매 프레임마다 호출되는  Update()에서 처리

⇒ 키를 언제 누르더라도 대응 가능하도록



##### Input 클래스

사용자의 키 입력을 판정하는 클래스

•Input.GetAxis(“Horizontal”) : 좌우 이동키의 이동 방향 

•Input.GetAxis(“Vertical”) : 앞뒤 이동키의 이동 방향 

•Input.GetKeyDown() : 특정한 키를 눌렀는 지 여부 

•Input.GetKeyUP() : 특정한 키에서 손가락이 떨이진 순간에만 

•Input.anyKeyDown: 아무 키나 눌린 순간에만

•Input.GetButtonDown() : 특정한 키나 버튼을 눌렀는 지 여부 •Input.GetMouseButtonDown(BUTTON) : 마우스버튼을 눌렀는 지 여부

Input.GetMouseButtonUP(BUTTON) :

BUTTON

0:왼쪽 버튼

1:오른쪽 버튼

2:휠

•Input.GetMousePosition :화면상에서 마우스 포인터의 위치를 반환

• Input.GetTouch() : 터치스크린 화면을 눌렀는 지 여부



##### Input.GetKey(KeyCode.<입력받을 키>)

키보드의 특정 키가 눌렸는 지 판정

KeyCode.Space - 스페이스 바

KeyCode.Return -엔터



KeyCode.UpArrow - ↑

KeyCode.DownArrow - ↓

KeyCode.LeftArrow - ←

KeyCode.RightArrow - →



KeyCode.Escape - ESP

KeyCode.BackSpace - 백스페이스



KeyCode.X - X

KeyCode.S - S

KeyCode.Alpha1 -1(!)

KeyCode.F1 - F1



### 4) 메쉬 Mash

게임 오브젝트 모델링

물체는 정점(Vertex), 선(Edge), 면(Face)로 구성

e.g) 정육면체는 8개의 정점,12개의 선,12개의 면으로 구성



### 5) Transform 클래스

​	물체를 이동하거나 회전할 때 사용한다.

##### Translate_이동

 	Object.transform.Translate(이동거리);

##### Rotate_회전

 	Object.transform.Rotate(x회전각 ,y회전각 ,z회전각);

##### localScale_축소/확대

​	Object.transform.localScale = Vector3(sx,sy,sz);

###### 적용 예

![image-20221012181913732](C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20221012181913732.png)

키보드에서 키를 입력받으면 이동하는 것.

위에 코드에 있는 Time.deltaTime은 왜 있는 걸까?



##### Time.deltaTime

직전 프레임과 현재 프레임 사이의 소요시간을 뜻한다.

###### 직전 프레임↔현재프레임 소요시간

매 프레임 이동거리 →  속도*Time.deltaTime

속도 부분에는 숫자 적으면 된다. 



모든 물체는 플랫폼, 즉 기기나 실행되는 환경에서

항상 일정한 속도로 이동하게 하려고 사용하는 deltaTime 을 사용함.







### 6) 물리 기능 추가

유니티에서 중력 추가 방법

Component -> Physics -> Rigidbody

여기서 Rigidbody 는?

####  Rigidbody

물리적인 특성을 부여할 수 있게 한다.

물리적인 특성은 외력 외부의 힘? 중력과 마찰



##### 속성

이미지_유니티 화면에서 보여지는 Rigidbody창

![image-20221012190902856](C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20221012190902856.png)



###### Mess : 오브젝트의 질량

###### Drag(공기저항)

: 오브젝트가 힘에 의해 움직일 때 공기 저항이 영향을 미치는 정도

​          0 - 공기 저항이 없다. ∞ - 오브젝트가 즉시 정지

###### Angluar Drag(회전 공기 저항_회전하는 물체만 적용)

: 오브젝트가 토크로 회전할 때 공기 저항이 영향을 미치는 정도

###### Use Gravity

: 중력의 영향을 받는다 ⩗

 중력의 영향을 받지 않는다. 체크표시 안함.

###### Is Kinematic

:활성 시 물체에 가해지는 힘의 크기와 방향은 계산하지 않음.

물리엔진의 기능을 무효로 (물리 효과를 추가하지 않은거다.)

###### Interpolate(보정)

:물체의 움직임이 지나치게 끊겨 보일 때

 프레임의 이동거리가 길때

Interpolate속성

• None - 보정을 안한다는 뜻

•Interpolate - 이전 다음 프레임의 Transform을 기반으로 근사

•Eetapolate - 이전 그 이전 프레임의 Transform을 기반으로 근사

e.g) 발로란트할때 60프레임일때랑 

​                  			200프레임일때 내 게임 실력 생각하기.

 진짜로 프레임에 따라 게임 실력은 차이나는 듯 이건 어쩔 수 없음 ㅜ

발로란트 하고 싶당



###### Collision Detection

:충돌이 일어나는 지 검사 후에, 방식에 따름

• Discreate - 현재 프레임 위치만 검사

​                    - Tunneling 문제

• Continuous 

- 이전 프레임과 현재 프레임 사이의 이동 궤적을 바탕으로 충돌 검사
- 안정적인 충돌 검사 가능하다
- 계산량 증가한다.
- Rigidbody를 가진 물체엔 Discrete충돌 검사, Rigidbody가 없는 물체는 Continuous 충돌 검사

• Continuous Dynamic 

- 압도적인 계산량

- Continuous 충돌 검사  

  Continuous나 Continuous Dynamic이 적용된 물체 

   Rigidbody가 없는 물체 

- Discrete가 적용된 물체엔 Discrete 충돌 검사

• Constraints - 외력에 의한 움직임에 제약을 줄 때 사용한다.

- Freeze Position 

  • 선택된 축 방향 이동불가 

- Freeze Rotation 

  • 선택된 축 중심 회전불가



###### Tunneling 문제

A와 B 두 물체가 있을 때, A의 속력이 너무 빨라서 프레임당 움직이는 이동하는 거리가 너무 늘어난다. B와 충돌하는 충돌검사가 일어나지 않는다.

두 물체의 picth가 다름

 해결방식

Continuous방식을 사용하면 된다. ->이동하는 궤적을 바탕으로 계산



### 7)GetComponent<ComponentName>()

componentName에 해당하는 구성요소를 찾아 반환

 • 용법 

▪ (this.)GetComponent() 

​	현재 스크립트에 연결된 물체에서 찾을 경우에만 허용

 ▪ (this.)gameObject.GetComponent() 

▪ (this.)transform.GetComponent()

 • 다른 게임 오브젝트에 속한 스크립트를 참조하려면 GetComponent() 메서드 사용함





