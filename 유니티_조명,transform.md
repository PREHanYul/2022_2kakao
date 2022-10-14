#### 컴퓨터 게임의 정의

일정한 규칙 아래 상호간의 경쟁을 통하여 승부를 낼 수 있는 것

##### 게임의 속성

재미,규칙,갈등과 경쟁,선택,능동적인 참여,서사성,목표,비선형성

#### Inspector에서 속성 변경이 가능



#### 유니티 대표적인 조명



##### point light 점광원

정해진 위치에서 사방으로 퍼져나가는 빛

물체까지의 거리에 따라 빛의 세기가 감소한다.

##### Directional Light 방향성 광원

태양빛을 단순화한 광원으로, 씬 안에 게임 오브젝트가 어디에 있든지 상관없이 일정한 각도와 세기로 빛을 비춰준다.

방향만 존재.

##### Spotlight 스포트 라이트

정해진 위치에서 일정한 방향으로 퍼져나가는 빛

빛이 방사되는 한계각도(Spot angle) 존재



#### 유니티에서 외부 편집기 연결하는 방법

edit->preferences

Analysis->External Tool클릭

External Script Editor에서 Visual Studio 버젼 변경.



###### 나에게 필요한 이유

내 환경이 이상한건지 자꾸만 삭제한 Visual Studio 2017이 연결된다. 아무래도 예전에 유니티 환경 작업할때 설정된듯,,,

그래서 스크립트 작성할 때마다 마우스 클릭만 하면 강제종료됌.



#### 유니티 이름 선언 규칙

단어가 바뀔 때마다 대문자.

변수:소문자로 시작

함수 및 클래스: 대문자로 시작.



#### Transform클래스

모든 물체는 플랫폼, 즉 기기나 실행되는 환경에 항상 일정한 속도로 이동한다.

##### => deltaTime 사용.

이동 Object.transform.Translate(이동거리);

회전 Object.transform.Rotate(x회전각 ,y회전각 ,z회전각);

축소/확대Object.transform.localScale = Vector3(sx,sy,sz);



##### Time.deltaTime

직전 프레임과 현재 프레임 사이의 소요시간을 말한다.

매 프레임 이동거리 -> 속도*Time.deltaTime

