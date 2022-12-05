# Win32

## 개요

***Unreal Engine*** 프로그래밍을 하기에 앞서 ***DirectX*** 프로그래밍을,  
***DirectX*** 프로그래밍을 하기에 앞서 ***Win32*** 프로그래밍 기초를 다지려고 한다.

유용한 링크 위주로 올리되, 실습 코드나 내 것으로 정리한 내용도 같이 올리면 좋을 듯.  
Visual Studio 각종 단축키나 설정팁 등 자잘한 내용도 잘 기록해놓을 것.

처음 보고 단번에 이해할 수 있는 내용들이 아니다. 자주 읽어 버릇해 익숙해지도록 하자.


## Index

* ### [Tips](#tips-1)

    * #### [Visual Studio](#visual-studio-1)
    * #### [Cmd](#cmd-1)

* ### [Documents To Read](#documents-to-read-1)

---

## Tips

* ### Visual Studio

    * #### [단축키](https://learn.microsoft.com/en-us/visualstudio/ide/default-keyboard-shortcuts-in-visual-studio?view=vs-2022)
        * 단축키 안 먹힐 때 초기화: *Tools > Options > Environment > Keyboard > Reset > 예(Y) > OK*

    * #### Markdown
        * VS Code와는 다르게 따로 Extension 설치해줘야 함
        * *Extensions > Manage Extentions > 'Markdown Editor v2' 설치*
    * #### 자동 정렬
        * Ctrl + (K, D)

* ### Cmd
    * #### Background exec
        ```cmd
        > start .\main.exe
        ```

---


## Documents To Read

- [ ] [인코딩 설정](https://learn.microsoft.com/en-us/visualstudio/ide/how-to-save-and-open-files-with-encoding?view=vs-2022)
- [ ] [DirectX 전제 조건](https://learn.microsoft.com/en-us/windows/win32/direct3dgetstarted/pre-requisites-for-developing-a-tailored-c---with-directx-app)
- [ ] [DirectX 3D 11](https://learn.microsoft.com/en-us/windows/win32/directx)
- [ ] [C++/WinRT](https://learn.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/)
- [ ] [Windwos UWP Game programming](https://learn.microsoft.com/en-us/windows/uwp/gaming/getting-started)
- [ ] [Win32 프로그래밍 기초](https://learn.microsoft.com/en-us/windows/win32/learnwin32/learn-to-program-for-windows)
- [ ] [DirectX 게임 개발 기초](https://learn.microsoft.com/en-us/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game)
- [ ] [POCU C++ 코딩 표준](https://docs.popekim.com/ko/coding-standards/pocu-cpp)
- [ ] [C++ Core Guidelines - NL.5: Avoid encoding type information in names](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#nl5-avoid-encoding-type-information-in-names) (스크롤 압박 주의)