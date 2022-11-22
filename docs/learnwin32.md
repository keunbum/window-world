# Learn Win32

영어로 쓰자니 본문을 그대로 옮길 것 같고, 한글로 적자니 어색하고.. ㅠㅠ

본문을 옮겨 적는 게 시간을 넘 많이 잡아먹어서 ㄹㅇ 핵심만 적어야 할 듯..
그냥 대강 읽고 넘어가면 되는 내용에 대해서 시간 버리지 말 것.


# Index

* ## [What Is a Window?](#what-is-a-window?-1)
    * ### [What Is a Window?](#what-is-a-window?-2)
	* ### [Parent Windows and Owner Windows](#parent-windows-and-owner-windows-1)
	* ### [Window Handles](#window-handles-1)
	* ### [Screen and Window Coordinates](#screen-and-window-coordinates-1)

* ## [Reference](#reference)

---

# What Is a Window?

## What Is a Window?

운영체제 이름에서 알 수 있듯이 Windows에 있어 Window는 중요하다.

![Windows_Example](https://learn.microsoft.com/en-us/windows/win32/learnwin32/images/window01.png)

이런 류의 윈도우를 *application window* 또는 *main window*라 부른다.
대개 **frame**, **title bar**, **최소화**와 **최대화** 버튼, 그밖에 다른 표준 UI 요소들로 이루어져 있다.
**frame**은 *non-client area*라고 부른다. 운영체제가 윈도우의 그 부분(겉 테두리. 틀)을 담당하기 때문이다.
**frame** 내부는 프로그램이 운용하기에 *client area*라고 부른다.

여기, 또 다른 타입의 윈도우가 있다.

![OK Window](https://learn.microsoft.com/en-us/windows/win32/learnwin32/images/window02.png)

흥미로운 건 버튼이나 편집 박스 등의 **UI 컨트롤**들 또한 그 자체로 윈도우라는 점이다.
**UI control**이 **application window**와 다른 점은 그 자체로는 컨트롤이 없다는 것.
**control**은 **application window**에 의해 상대적으로 위치한다. 윈도우를 움직이면 나머지 요소들이 같이 움직이지 않는가?
**control**과 **application window**는 서로 소통할 수 있다고 한다.(**application window**가 **button**으로부터 클릭 알림을 받는 것이 한 예)

이제는 윈도우를 떠올릴 때 단순히 응용 프로그램 창이 아니라, 프로그래밍 구조로 봐야 한다:

* 스크린의 특정 부분을 점유한다.
* 특정 순간에 보일 수도 안보일 수도 있다.
* 자기 자신을 어떻게 드로잉하는지 안다.
* 사용자나 운영체제에 의한 이벤트에 반응한다.


## Parent Windows and Owner Windows

위에서 언급한 **UI 컨트롤**은 **application window**의 *child window*,
반대로 **application window**는 **UI control**의 *parent window*이다.
**parent window**는 **child window**에 좌표계를 제공한다. 부모 윈도우를 가지면 윈도우의 모습에 영향을 미치는데,
예를 들어 자식 윈도우의 일부가 부모 윈도우의 경계 밖으로 나갈 수 없도록 자식 윈도우가 일부 잘린다.

또 하나의 관계로 **application window**와 **dialog window**를 들 수 있다.
응용 프로그램이 대화 상자를 띄울 때 **application window**는 *owner window*, **dialog**는 *owned window*가 된다.
**owned window**는 항상 **owener window** 앞에 나타나며, **owner window**가 최소화되거나 닫히는 경우 **owned window** 또한 같이 없어진다.

아래는 '두 개의 버튼을 가진 대화 상자'를 띄운 응용 프로그램 창 사진이다.

![Owner and Owned Windows](https://learn.microsoft.com/en-us/windows/win32/learnwin32/images/window03.png)

여기서 각 window들이 Owner/Owned 관계인지 아니면 Parent/Child 관계인지 잘 구분하자.

![Windows Relation Diagram](https://learn.microsoft.com/en-us/windows/win32/learnwin32/images/window04.png)


## Window Handles

윈도우는 객체이다. (내부적으로 코드와 데이터를 가지고 있겠지만 C++ 클래스가 아니다.)
프로그램은 *handle*이라 불리는 값을 통해 윈도우를 참조한다. **handle**은 불투명한(?) 타입이라고 한다.
분명하게 인지해야할 점은 이는 단순히 운영체제가 객체를 식별하기 위해 사용하는 숫자에 불과하다는 것.
운영체제는 생성된 모든 윈도우를 참조하는 테이블을 가지고 있다. 이 테이블에서 윈도우를 참조하기 위해 **handle**을 사용한다.
(내부적으로 정확히 어떻게 동작하는지는 아직은 굳이 알 필요 없을듯..)
**HWND**가 이 **handle**의 타입이며("에이치-윈도우"라 발음하는듯?)
이 **handle**을 생성하기 위해 [CreateWindow](https://learn.microsoft.com/en-us/windows/win32/directshow/cbasewindow-docreatewindow)나 [CreateWindowEx](https://learn.microsoft.com/en-us/windows/win32/api/winuser/nf-winuser-createwindowexa)를 호출한다.

**Window**를 다루는 함수를 호출한다면 **HWND** 값을 인자로 넘겨주면 된다.

```c++
BOOL MoveWindow(HWND hWnd, int X, int Y, int nWidth, int nHeight, BOOL bRepaint);
```

파라미터에서 **HWND**가 포인터로 선언되지 않았음에 유의하자. 


---

## Screen and Window Coordinates


(모바일 프로그래밍에서 컴포넌트 배치하는 거랑 비슷한듯?)

![Coordinates](https://learn.microsoft.com/en-us/windows/win32/learnwin32/images/coordinates01.png)


---

# Reference

* [learnwin32](https://learn.microsoft.com/en-us/windows/win32/learnwin32/learn-to-program-for-windows)