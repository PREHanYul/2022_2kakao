# Sky Box

unity

스카이 박스는 전체 씬이 둘러사는 래퍼로 지오메트리 너머의 월드가 어떻게 생겼는지 보여주는 것.

-> 그냥 땅바닥말고 하늘 모형 우리가 하늘을 볼때 계속 이어지는 느낌으로.



직접 그림을 그려서 재질을 입혀도 되고 

asset store에서 가져와도 됌.



적용방법



a.재질을 만들고, Shader에서 6slided선택하면

Front, Back, Left, Right, Up, Down 의 6개 있음

각각의 이미지 넣고 저장하면 된다.



b.재질을 만들고, Shader에서 skybox/cubemap선택 후

이미지를 드래그하여  (참고로 저 파일 위치는 에셋스토어에서 임포트한 파일인데 제작자가 설정한 이름임.)



window -> Rendering -> Lighting

skybox Material에서 자신이 만든 재질 선택 (적용 완료)