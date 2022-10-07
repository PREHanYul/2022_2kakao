# 디지털 영상 처리

10월5일커밋

###### -디지털 영상을 처리하려면

디지털 영상을 visual C++를 이용해 입력 받은 뒤 일정한 루틴에 따라

처리한 후 그 결과를 다시 디지털 영상 파일로 저장하는 과정이 필요하다.



###### -이 부분 기억하기 (왜냐면 만들때 필요하니깐)

RAW포맷의 디지털 영상에는 0~255로 구성된 

8비트 그레이 레벨이 있어서 c언어의 unsigned char(0~255,8비트)로 저장가능

 

1.MFC 프로젝트 작성

2.OnOpenDocument함수 재정의

​	2-1. [파일]-[열기] 메뉴 클릭 후 대화상자 실행

​	2-2. [만든 파일]선택 후, 오른쪽 마우스 클릭

3.구성 속성에서 고급을 클릭 후,문자 집합찾기

​	3-1. ▽이런 표시 눌러서 "멀티바이트 문자 집합 사용"으로 변경

4.workbench에서 클래스 뷰 선택

​	4-1.CImageProcessingDoc선택후, properties에서 Overrides선택(재정의)

​	4-2. 아래와 같은 코드가 생성된다.

BOOL CImageProcessing2022208023KHYDoc::OnOpenDocument(LPCTSTR lpszPathName)
{
	if (!CDocument::OnOpenDocument(lpszPathName))
		return FALSE;

	// TODO:  여기에 특수화된 작성 코드를 추가합니다.
	
	return TRUE;
}



5. 영상을 입력 받기 위해서 변수를 추가하기

   5-1. ClmageProcessingDoc 클릭후, 추가 선택

   5-2. 추가에서 변수 추가(B)선택하고

   |                         | Variable Type   | Variable Name | Access |
   | ----------------------- | --------------- | ------------- | ------ |
   | 입력 영상을 위한 포인터 | unsigned char * | m_InputImage  | Public |
   | 입력 영상의 가로축 크기 | int             | m_width       | Public |
   | 입력 영상의 세로축 크기 | int             | m_height      | Public |
   | 입력 영상의 전체 크기   | int             | m_size        | Public |

   

6.OnOpenDocument로 이동한 뒤 함수 재정의하기.

​	6-1. 4-2에서 봤던 부분에서

CFile File; //파일 객체 선언

	File.Open(lpszPathName, CFile::modeRead | CFile::typeBinary);
	// 파일 열기 대화상자에서 선택한 파일을 지정하고 읽기 모드 선택
	// 이 책에서는 영상의 크기 256*256, 512*512, 640*480만을 사용한다.
	if (File.GetLength() == 256 * 256) { // RAW 파일의 크기 결정
		m_height = 256;
		m_width = 256;
	}
	else if (File.GetLength() == 512 * 512) { // RAW 파일의 크기 결정
		m_height = 512;
		m_width = 512;
	}
	else if (File.GetLength() == 640 * 480) { // RAW 파일의 크기 결정
		m_height = 480;
		m_width = 640;
	}
	else {
		AfxMessageBox("Not Support Image Size"); // 해당 크기가 없는 경우
		return 0;
	}
	m_size = m_width * m_height; // 영상의 크기 계산
	m_InputImage = new unsigned char[m_size];
	// 입력 영상의 크기에 맞는 메모리 할당
	for (int i = 0; i < m_size; i++)
		m_InputImage[i] = 255; // 초기화
	File.Read(m_InputImage, m_size); // 입력 영상 파일 읽기
	File.Close(); // 파일 닫기

작성하기.

*AfxMessageBox알림창 띄우기



7.CImageProcessingView 클래스로 이동 후, OnDraw 함수를 재정의버튼 클릭하기



![](C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20221004211021115.png)



8.void CImageProcessing2022208023KHYView::OnDraw(CDC* pDC)
{
	CImageProcessing2022208023KHYDoc* pDoc = GetDocument();
	ASSERT_VALID(pDoc);
	if (!pDoc)
		return;

	int i, j;
	unsigned char R, G, B;
	for (i = 0; i < pDoc->m_height; i++) {
		for (j = 0; j < pDoc->m_width; j++) {
			R = G = B = pDoc->m_InputImage[i * pDoc->m_width + j];
			pDC->SetPixel(j + 5, i + 5, RGB(R, G, B));
		}
	}
}

보이는 사진에 이 코드 써넣기



9. raw파일의 사진이 열리는지 확인하기

   

10. ![image-20221004211311862](C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20221004211311862.png)