# Challenge_08_SimpleWebBrowser
## 심플 웹 브라우저

간단한 웹 브라우저의 역할을 하는 어플리케이션이다.


## 기능

* 홈으로 가기 (여기서 "홈"은 https://www.google.com을 Default Url로 설정하였다. 따로 홈을 변경하는 기능은 제공하지 않는다.)
* 이전 페이지 (이전 페이지가 존재하지 않을 경우 버튼 disable)
* 다음 페이지 (다음 페이지가 존재하지 않을 경우 버튼 disable)
* 주소창에서 'http://'를 제외하고 'www'부터 작성하여 이동하면 자동으로 http://를 붙인 상태로 이동
* SwipeRefreshLayout 적용
* 웹사이트의 로딩 정도를 확인할 수 있도록 ContentLoadingProgressBar 적용


## 활용 기술

* Request runtime permissions
  * 프라이버시를 침해할 위험이 커 Dangerous permission에 지정된 마이크에 접근에 사용
* CustomView
  * 음성을 시각화 하는데에 사용
* MediaRecorder
  * 마이크를 통해 소리를 녹음하는데에 사용


# 실행화면

<img src="https://user-images.githubusercontent.com/74666576/152837471-1d4afdc7-c407-4051-bc59-18cc1d3c5326.jpg" width="270" height="500">
<img src="https://user-images.githubusercontent.com/74666576/152838123-e5103f60-249c-4b55-9b5f-61d9a916768e.gif" width="270" height="500">
