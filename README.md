# Challenge_08_SimpleWebBrowser
## 심플 웹 브라우저

간단한 웹 브라우저의 역할을 하는 어플리케이션이다.


## 기능

* 홈으로 가기 (여기서 "홈"은 'http://www.google.com' 을 Default Url로 설정하였다. 따로 홈을 변경하는 기능은 제공하지 않는다.)
* 이전 페이지 (이전 페이지가 존재하지 않을 경우 버튼 disable)
* 다음 페이지 (다음 페이지가 존재하지 않을 경우 버튼 disable)
* 주소창에서 'http://' 를 제외하고 'www'부터 작성하여 이동하면 자동으로 'http://' 를 붙인 상태로 이동
* SwipeRefreshLayout 적용
* 웹사이트의 로딩 정도를 확인할 수 있도록 ContentLoadingProgressBar 적용
* __이번 차트에서는 'https://' 프로토콜과 같은 보안관련 기능은 다루지 않도록 한다.__


## 학습 내용

### WebView
* 인터넷 브라우저인 만큼 Internet permission이 요구된다.
  * [Manifest]
  ```kotlin 
  <uses-permission android:name="android.permission.INTERNET"/>
  ```
  인터넷 권한을 부여해준다.
* WebView 사용 시 기본적으로 http프로토콜을 사용하면 웹페이지 연결이 불가능하다. 이를 사용할 수 있도록 설정해준다.
  * [Manifest] <application
                            
  ```kotlin
  android:usesClearTextTraffic="true"
  ```   
* 아직 브라우저를 사용하지 못한다. 이 상태에서 webview를 실행하면, default 웹 브라우저로 url이 전송되어 따로 실행된다.(ex: chrome)
  * 이를 해결하기 위해서는 webview를 새로 생성하는 webview로 override하면 된다.
  
  ```kotlin
  webView.webViewClient = WebViewClient()
  webView.loadUrl("http://www.google.com")
  ```
* 이제 webview에서 화면은 잘 불러온다. 하지만 여전히 버튼들이 눌러지진 않는다.
  * 이유는 해당 web에 구현되어있는 JavaScript가 현재의 webview에서는 작동하지 않기 때문이다. (보안상 이슈)
  * 해결은 간단하다. webView를 초기화 할때 javaScript를 사용하도록 설정한다.
  ```kotlin
  webView.webViewClient = WebViewClient()
  webView.settings.javaScriptEnabled = ture
  webView.loadUrl("http://www.google.com")
  ```
          
### Navigation
* 홈버튼
  ```kotlin
  webView.loadUrl("http://www.google.com")
  ```
* 이전페이지, 다음페이지
  * webView에서 이전페이지와 다음페이지는 따로 스택을 사용하지 않아도 간단히 구현이 가능하다.
  ```kotlin
  webView.goBack()
  webView.goForward()
  ```
* BackButton 클릭시 (기기의 물리적인 뒤로가기 버튼)
  * BackButton 클릭시 이전페이지가 존재하면 이전페이지로 이동, 존재하지 않으면 앱 종료
  ```kotlin
  override fun onBackPressed() {
    if(webView.canGoBack()) {
      webView.goBack()
    } else {
      super.onBackPressed()
    }
  }
  ```
                           
                            
# 실행화면

<img src="https://user-images.githubusercontent.com/74666576/152837471-1d4afdc7-c407-4051-bc59-18cc1d3c5326.jpg" width="270" height="500">
<img src="https://user-images.githubusercontent.com/74666576/152838123-e5103f60-249c-4b55-9b5f-61d9a916768e.gif" width="270" height="500">
