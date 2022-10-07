# 디지털 영상 처리 

10월6일 커밋

###### -OnSaveDocument 함수를 이용한 파일 출력

Visual C++에서 처리된 영상 데이터는 1차원이나 2차원 형태의 배열 데이터로 존재한다.

이 배열 데이터를 확장자가 raw인 파일로 출력하려면 프로그램이 필요하다.

이것을 지원하는 것이 바로 OnSaveDocument.



1. ClmageProcessingDoc클래스 선택 후 재정의하기

2. 속성에서 OnSaveDocument클래스 함수 추가하기

   <Add>OnSaveDocument표시를 선택하면 된다.

3.  추가된 것을 확인.

   BOOL CImageProcessing2022208023KHYDoc::OnSaveDocument(LPCTSTR lpszPathName)
   {
   	// TODO: 여기에 특수화된 코드를 추가 및/또는 기본 클래스를 호출합니다.

   	return CDocument::OnSaveDocument(lpszPathName);

   }

라고 보여야한다.

4. OnSaveDocument 함수 재정의하기 (3.부분에)

   CFile File; // 파일 객체 선언
   	CFileDialog SaveDlg(FALSE, "raw", NULL, OFN_HIDEREADONLY);
   	// raw 파일을 다른 이름으로 저장하기를 위한 대화상자 객체 선언
   	if (SaveDlg.DoModal() == IDOK) {
   		// DoModal 멤버 함수에서 저장하기 수행
   		File.Open(SaveDlg.GetPathName(), CFile::modeCreate |
   			CFile::modeWrite);
   		// 파일 열기
   		File.Write(m_InputImage, m_size); // 파일 쓰기
   		File.Close(); // 파일 닫기
   	}

   

   5. 결과 확인하기. LENA256파일을 LENA256_1 저장하기

      ![image-20221004212949415](C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20221004212949415.png)

   

MFC(2)

###### -영상 축소하기(다운 샘플링, DownSampling)

디지털 영상을 축소하는 가장 간단한 방법

다운 샘플링은 원 영상의 값을 일정한 좌표 단위로 버리는 것.

디지털 영상은 2차원이므로 수평축 샘플링과 수직축 샘플링이 모두 되어야 한다.



###### 실습

계속 하던 파일 열고 시작하기.

1. 리소스뷰 클릭. 

2. MENU 파일 클릭 후 IDR_ImageProcessingTYPE 메뉴 더블 클릭

3. 파일이 하나 열리는 데 거기에 여기에 입력에 "영상처리"입력한다.

4. 영상처리 아래에 "DownSample"입력한다. 

   4-1. 속성에 들어간 후 메뉴 편집기에서 ID 이름 알아볼 수 있도록 변경

   (ID_DOWN_SAMPLING) 캡션이름도 바껴있을거임.

5. 팝업창에서 이벤트 처리기 추가하기.

   5-1. ◼ Message type: COMAND ◼ Class list: CImageProcessingView 선택 후 확인버튼 눌러서 생성.

   (왜 갑자기 Visual2022가 꺼졌을까요? 하...)

   

   6.“리소스 뷰＂창에서 [ImageProcessing resources]-[Dialog] 폴더 선택 → 바로가기 메뉴 [Dialog 삽입] 클릭 → 새 [Dialog] 대화상자가 추가됨

   6-1. 내 노트북 기준으로 도구 상자는 오른쪽 바에 붙어있음.

   6-2. static text과 Edit Control 넣기 그리고 예쁘게 UI설정하기.

   6-3. 대화상제 삽입된 각 항목의 속성을 밑이 표와 같이 설정하기.

   |                 | ID          | Caption         |
   | --------------- | ----------- | --------------- |
   | Dialog          | IDD_DIALOG1 | DownSample Rate |
   | Text Properties | IDC_STATIC  | DownSample Rate |
   | Edit Properties | IDC_EDIT1   |                 |

   

   

   7. "Edit control" 더블 클릭하면 MFC클래스 추가 화면이 표시된다.

      7-1. 클래스 이름(L) CDownSampleDlg 설정

      7-2. 대화상자 ID(D) IDD_DIALOG1 설정 

      7-3. 자동화 지원 포함에 체크표시 후에 확인 누르기.

   8. "Edit control" 클릭 후 ,변수추가하기

   여기까지가 메뉴 설정이고 이제 누르면 진짜로 작아지도록

   프로그램 작성해야한다.

**![image-20221004221959002](C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20221004221959002.png)**

![image-20221004222124043](C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20221004222124043.png)

위에 사진은 CImageprocessing.Doc 에 함수 추가 한것.



9.  CImageprocessing.Doc  변수 추가 해야함.

   9-1.

   |                         | Variable Type   | Variable Name | Access |
   | ----------------------- | --------------- | ------------- | ------ |
   | 입력 영상을 위한 포인터 | unsigned char * | m_OutputImage | Public |
   | 입력 영상의 가로축 크기 | int             | m_Re_width    | Public |
   | 입력 영상의 세로축 크기 | int             | m_Re_height   | Public |
   | 입력 영상의 전체 크기   | int             | m_Re_size     | Public |

   

10. OnDownSampling함수 작성하기

 	void CImageProcessing2022208023KHYDoc::OnDownSampling()
{
	int i, j;
	CDownSampleDlg dlg;
	if (dlg.DoModal() == IDOK) // 대화상자의 활성화 여부
	{
		m_Re_height = m_height / dlg.m_DownSampleRate;
		// 축소 영상의 세로 길이를 계산
		m_Re_width = m_width / dlg.m_DownSampleRate;
		// 축소 영상의 가로 길이를 계산
		m_Re_size = m_Re_height * m_Re_width;
		// 축소 영상의 크기를 계산
		m_OutputImage = new unsigned char[m_Re_size];
		// 축소 영상을 위한 메모리 할당
		for (i = 0; i < m_Re_height; i++) {
			for (j = 0; j < m_Re_width; j++) {
				m_OutputImage[i * m_Re_width + j]
					= m_InputImage[(i * dlg.m_DownSampleRate * m_width) + dlg.m_DownSampleRate * j];
				// 축소 영상을 생성
			}
		}
	}
}

11. view 클래스의 OnDownSampling함수 작성

 void CImageProcessing2022208023KHYView::OnDownSampling()
{
	CImageProcessing2022208023KHYDoc* pDoc = GetDocument(); // Doc 클래스 참조
	ASSERT_VALID(pDoc);
	pDoc->OnDownSampling(); // Doc 클래스에 OnDownSampling 함수 호출
	Invalidate(TRUE); // 화면 갱신 (TRUE: 화면 배경색을 포함해서 재출력)
	// 화면 갱신 (FALSE: 배경색은 그냥 두고 그 이외의 부분 재출력)

}



12. view클래스의 OnDraw함수에

    // 축소된 영상 출력
    	for (i = 0; i < pDoc->m_Re_height; i++) {
    		for (j = 0; j < pDoc->m_Re_width; j++) {
    			R = pDoc->m_OutputImage[i * pDoc->m_Re_width + j];
    			G = B = R;
    			pDC->SetPixel(j + pDoc->m_width + 10, i + 5, RGB(R, G, B));
    		}
    	}

    추가하기.

13. 실행하기

    ![image-20221004223620219](C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20221004223620219.png)



하면서 느낀 점

: 오류가 발생하면 오타가 있는지 확인하기

  오타가 없다면 괄호들이 제대로 있는지 확인하기

 그래도 오타가 있다면 그건 나도 모르지.