# Create your Kotlin Multiplatform app

공유 로직 및 기본 UI 튜토리얼을 사용하여 Kotlin 멀티플랫폼 앱 만드세요.

Kotlin 멀티플랫폼 기술은 크로스 플랫폼 프로젝트 개발을 간소화합니다. Kotlin 멀티플랫폼 애플리케이션은 iOS, Android, macOS, Windows, Linux 웹 등 다양한 플랫폼에서 작동할 수 있습니다.

주요 kotlin 멀티플랫폼 사용 사례 중 하나는 모바일 플랫폼 간 코드 공유입니다. iOS와 Android 앱간에 애플리케이션 로직을 공유하고 네이티브 UI를 구현하거나 플랫폼 API로 작업해야 하는 경우에만 플랫폼별 코드를 작성할 수 있습니다.


## Set up th environment

- android Studio에 Kotlin Multiplatform 플로그인을 설치합니다.
- iOS 앱을 개발할 계획이라면 XCode를 최소 한 번 실행하고 이용약관에 동의해야 합니다.
- Kdoctor를 실행하여 설정에 문제가 있는지 확인합니다.

### (Mac) Check your environment

잘 작동는지 확인하려면 KDoctor 도구를 설치하고 실행하세요.

1. Homebrew를 사용하여 도구를 설치한다.
```terminal
brew install kdoctor
```
2. 설치가 완료되면 `KDoctr`를 호출한다.
```terminal
kdoctor
```
3. KDoctor가 환경을 점검하는 동안 문제를 진단하는 경우 출력에서 문제와 가능한 해결 방법을 검토하세요:
- 실패한 검사([X])를 수정합니다. 기호뒤에서 문제 설명과 가능한 해결 방법을 찾을 수 있습니다.
- 경고([!])와 성공 메시지([v])를 확인합니다. 유용한 참고 사항과 팁도 포함될 수 있습니다.


> 이런 오류가 나오면 Xcode 설치 후 실행해 주면 된다.
>``` 
>[✖] Xcode
> ✖ Xcode requires to perform the First Launch tasks
>   Launch Xcode and complete setup
>```
> CocoaPods 설치완 관련된 KDoctor의 경고는 무시해도 된다. 

## Create the project with a wizard

1. [Kotlin Multiplatform wizard](https://kmp.jetbrains.com/)를 열어줍니다.
2. 새로운 프로젝트 탭에서 프로젝트 이름을 `GreetinKMP` 그리고 프로젝트 아이디를 `com.jetbrains.greeting`으로 바꿔줍니다.
3. Android 및 iOS 옵션이 선택되어 있는지 확인합니다.
4. iOS의 경우 UI를 기본적으로 유지하려면 UI공유 안 함 옵션을 선택합니다.
4. 다운로드 버튼을 클릭하고 결과 아카이브의 압축을 풉니다.

> 실행 후 와 같은 오류가나오면 안드로이드 스튜디오 버전을 올려주면 된다.
> ```
> The project is using an incompatible version (AGP 8.5.2) of the Android Gradle plugin. Latest supported version is AGP 8.2.2
> ```