# 🎬 박스오피스
![](https://hackmd.io/_uploads/r1MNQyh9n.png)
> 프로젝트 기간 23/07/24 ~ 23/08/04

## 📖 목차
1. [소개](#-소개)
2. [팀원](#-팀원)
3. [타임라인](#-타임라인)
4. [시각화된 프로젝트 구조](#-시각화된-프로젝트-구조)
5. [실행 화면](#-실행-화면)
6. [트러블 슈팅](#-트러블-슈팅)
7. [참고 링크](#-참고-링크)
8. [팀 회고](#-팀-회고)

</br>

## 🍀 소개
반다나 웨이들 디 훈과 커비 민트가 만든 박스오피스!
네트워크를 활용하여 만들기 위해 뚝딱뚝딱 공부하며 수리중🫠

* 주요 개념: `URL`, `Closure`

</br>

## 👨‍💻 팀원
| 😈커비 MINT😈 | 🐝반다나 웨이들 디 hoon🐝 |
| :--------: | :--------: |
|<Img src="https://hackmd.io/_uploads/rkdj-axo3.png" width="200"> | <Img src = "https://hackmd.io/_uploads/BkC3WTlsn.png" width="200"> | 
|[Github Profile](https://github.com/mint3382) |[Github Profile](https://github.com/Hoon94) |


</br>

## ⏰ 타임라인
|날짜|내용|
|:--:|--|
|2023.07.24.| - Swift Lint 시도 <br> - CocoaPod 사용 |
|2023.07.25.| - Data Decode Model 구현 <br> - Model 관련 Unit Test 작성 |
|2023.07.26.| - Closure 공식 문서 | 
|2023.07.27.| - URL Session 공식 문서 |
|2023.07.28.| - TCP/IP 공부 |

</br>

## 👀 시각화된 프로젝트 구조

### ℹ️ File Tree
````
BoxOffice
    ├──BoxOffice
    │       ├── Application
    │       │   ├── AppDelegate
    │       │   └── SceneDelegate
    │       ├── Controller
    │       │   └── ViewController
    │       ├── View
    │       │   ├── LaunchScreen
    │       │   └── Main
    │       ├── Model
    │       │   └── BoxOfficeData
    │       ├── Assets
    │       └── Info
    │    
    └──BoxOfficeTests
            ├── TestPlan
            ├── JsonDecodeTests
            └── Json
````


### 📐 Diagram
<p align="center">
<img width="800" src="https://hackmd.io/_uploads/SyRGRReo3.png">
</p>

</br>

## 💻 실행 화면 

추후 추가 예정

</br>

## 🧨 트러블 슈팅

1️⃣ **`Unit Test`에서 `json` 파일 사용** <br>
-
🔒 **🧐문제점🧐** <br>
- STEP 1에서는 `API` 서버와 실제 통신을 하지 않고 테스트하기 위해 `box_office_sample.json` 파일을 제공합니다. 제공된 `box_office_sample.json` 파일은 `Unit Test`의 목적으로만 사용될 거라는 예상 때문에 [`BoxOfficeTests`에 `json` 파일을 추가](https://stackoverflow.com/questions/46726498/add-test-assets-for-xctest)하였습니다. 새로운 `Asset Catalog`를 생성하고 `json` 파일을 추가 후 다음과 같이 사용하려고 하였습니다.

    ```swift
    guard let json = NSDataAsset(name: "box_office_sample") else {
        return
    }
    ```

    위와 같이 사용하면 파일을 불러오지 못하여 `json` 상수에 `nil`이 할당되는 문제가 있었습니다. 확인해 보니 사용하는 `Bundle`이 현재 `BoxOfficeTests` 번들이 아닌 점이 문제였습니다. 
    
🔑 **😆해결방법😆** <br>
- 문제를 해결하기 위해 사용하는 번들을 지정해 주었습니다.
    
    ```swift
    let bundle = Bundle(for: JsonDecodeTests.self)
    guard let json = NSDataAsset(name: "box_office_sample", bundle: bundle) else {
        return
    }
    ```
    
    `Bundle(for:)` 메서드를 사용하여 현재 지정된 클래스가 연결된 `NSBundle` 객체를 반환받고 이를 다시 넣어줌으로써 `box_office_sample`의 파일 위치를 특정하여 사용할 수 있었습니다.


</br>

## 📚 참고 링크
- [🍎Apple Docs: Equatable](https://developer.apple.com/documentation/swift/equatable)
- [🍎Apple Docs: URLSession](https://developer.apple.com/documentation/foundation/urlsession)
- [🍎Apple Docs: URLLoadingSystem](https://developer.apple.com/documentation/foundation/url_loading_system)
- [🍎Apple Docs: Fetching Website Data into Memory](https://developer.apple.com/documentation/foundation/url_loading_system/fetching_website_data_into_memory)
- [🍎Apple Docs: Bundle](https://developer.apple.com/documentation/foundation/bundle)
- [🍏Apple Archaive: About Bundles](https://developer.apple.com/library/archive/documentation/CoreFoundation/Conceptual/CFBundles/AboutBundles/AboutBundles.html#//apple_ref/doc/uid/10000123i-CH100-SW1)

</br>

## 👥 팀 회고
- [팀 회고 링크](https://github.com/mint3382/ios-box-office/wiki)
