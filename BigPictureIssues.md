# Big Picture Issues

## <a name="S-bpi"></a>Contents of this section\:

* [C++은 무엇입니까?](#Rbpi-1)
* [C++은 실용적인 언어입니까?](#Rbpi-2)
* [C++은 완벽한 언어입니까?](#Rbpi-3)
* [제로 오버헤드(Zero-overhead) 원칙이란 무엇인가요?](#Rbpi-4)
* [클래스(Class)의 장점은 무엇인가요?](#Rbpi-5)
* [객체지향(OO)이 왜 그렇게 중요한가요?](#Rbpi-6)

> ## <a name="Rbpi-1"></a>C++은 무엇입니까?

 C++은 시스템 프로그래밍 쪽으로 살짝 특화되어 있는 범용 프로그래밍 언어로,

* C언어보다 낫고
* 데이터 추상화를 지원하고(예: class)
* 객체 지향 프로그래밍을 지원하고(예: 상속)
* 일반화(generic) 프로그래밍을 지원하고(예: 재사용 가능한 일반 컨테이너(generic container)와 알고리듬)
* 함수형 프로그래밍을 지원합니다.(예: 템플릿 메타프로그래밍, 람다 함수, constexpr)

C++는 ISO 표준으로 정의되어 있고, 수십 년에 걸쳐 안정성을 제공하며, 크고 활발한 사용자 커뮤니티를 보유하고 있습니다. 더 자세한 내용은 책 [The C++ Programming Language](https://stroustrup.com/4th.html)와 논문 [Evolving a language in and for the real world: C++ 1991-2006](https://stroustrup.com/hopl-almost-final.pdf)을 참고하세요.  
C++가 [언제(when)](https://isocpp.org/wiki/faq/big-picture#when-invented), [왜(why)](https://isocpp.org/wiki/faq/big-picture#why-invented) 발명되었는지도 함께 확인해보세요.

> ### <a name="Rbpi-2"></a>C++은 실용적인 언어입니까?

네.  
C++은 실용적인 도구입니다. 완벽하지는 않지만 유용합니다.  
산업용 소프트웨어 세계에서 c++는 견고하고 성숙한주류 도구로 간주됩니다.  
폭넓은 산업 지원를 받고 있어 [전반적인 비즈니스 관점에서 볼 때](https://isocpp.org/wiki/faq/big-picture#biz-dominates-tech) '좋은' 선택이 됩니다.

> ### <a name="Rbpi-3"></a>C++은 완벽한 언어입니까?

아뇨.

C++은 완벽한 언어의 모습을 보여주기 위해 설계되지 않았습니다.  
현실 문제를 해결하기위한 실용적인 도구로 설계되었습니다.  
모든 실용적인 프로그래밍 도구가 그렇듯 몇 가지 단점이 있지만,  
완벽해질 때까지 계속 만지작거리는 것이 적절한 곳은 순수학 학문적 환경뿐입니다.  
그건 C++ 목표가 아닙니다.  

> ### <a name="Rbpi-4"></a>제로 오버헤드(Zero-overhead) 원칙이란 무엇인가요?

제로 오버헤드 원칙은 C++ 설계의 기본 원칙입니다. 이 원칙은 다음과 같습니다.  
- 사용하지 않는 것은 (시간적, 공간적)비용을 지불하지 않는다.
- 사용하는 것은 직접 코딩하더라도 더 나아질 수 없다.

즉, 새로운 기능을 사용하지 않는 기존 코드가 더 커지거나 느려지게 만드는 기능은 C++에 추가되어서는 안 되며, 컴파일러가 생성하는 코드가 프로그래머가 해당 기능 없이 직접 작성한 코드보다 품질이 떨어지는 기능 역시 추가되어서는 안 됩니다.

> ### <a name="Rbpi-5"></a>클래스(Class)의 장점은 무엇인가요?

클래스는 코드를 체계적으로 구성하고 프로그램 동작을 논리적으로 이해하는 데 도움을 줍니다.  
다르게 말하면, 클래스는 실수를 줄일 수 있고, 실수를 했을 때 버그를 쉽게 찾을 수 있도록 돕는 도구입니다.  
이러한 이유로 클래스는 유지 보수를 훨씬 더 쉽게 만들어 줍니다.

클래스는 코드에서 하나의 아이디어나 개념을 표현하는 역할을 하며, 객체는 그 개념의 구체적인 예시입니다. 클래스가 없으면 코드에서 데이터 항목과 함수 간의 관계를 일일이 추측해야 하지만, 클래스를 사용하면 이러한 관계가 명확해지고, 컴파일러도 이를 인식할 수 있습니다. 즉, 프로그램 설계가 코드 자체에 반영되므로 단순한 주석에 의존할 필요가 줄어듭니다.

잘 설계된 클래스는 사용자가 내부 동작을 몰라도 쉽게 사용할 수 있도록 깔끔하고 직관적인 인터페이스를 제공합니다. 만약 클래스 내부 구조를 감출 필요가 없다면, 예를 들어 사용자가 모든 데이터를 자유롭게 변경할 수 있어야 한다면, 그 클래스는 단순한 데이터 구조(Plain Old Data Structure, PIOD)로 취급될 수도 있습니다. 예를 들어 다음과 같은 Pair 구조체가 있습니다.

```CPP
struct Pair {
    Pair(const string& n, const string& v) : name(n), value(v) { }
    string name, value;
};
```

단순한 데이터 구조라 해도 생성자 같은 보조 함수를 활용하면 더욱 편리해집니다. 클래스를 설계할 때는 모든 객체가 항상 만족해야 하는 조건을 고려하는 것이 중요하며, 이를 클래스 불변식(invariant)이라고 합니다. 예를 들어, vector의 불변식은 (a) 내부적으로 요소를 가리키는 포인터를 유지해야 하며 (b) 요소의 개수를 나타내는 정수 값을 관리해야 합니다.  
생성자는 이러한 불변식을 설정하는 역할을 하며, 모든 멤버 함수는 불변식을 유지해야 합니다. 특히, 락(lock), 소켓(socket), 파일과 같은 리소스를 관리하는 클래스에서는 이러한 개념이 더욱 중요합니다. 예를 들어 파일을 관리하는 클래스는 항상 유효한 파일을 가리키는 포인터를 유지해야 합니다. 생성자는 파일을 열고, 소멸자는 파일을 닫아야 합니다.

```cpp
class File_handle {
public:
    File_handle(const char* n, const char* rw)
        { f = fopen(n,rw); if (f==nullptr) throw Open_failure(n); }
    ~File_handle() { fclose(f); } // destructor
    // ...
private:
    FILE* f;
};
```

클래스를 사용해 본 경험이 없다면, 이러한 개념이 다소 어렵게 느껴질 수도 있고, 클래스의 유용성을 과소평가할 수도 있습니다. 하지만 좋은 예제를 찾아보면 클래스를 더 효과적으로 활용할 수 있습니다. 예를 들어, [TC++PL](https://www.stroustrup.com/4th.html) 같은 책에는 다양한 예제가 포함되어 있으며, [A Tour of the Standard Library](https://www.stroustrup.com/3rd_tour2.pdf)에서는 C++ 표준 라이브러리를 활용하는 방법을 배울 수 있습니다. 대부분의 현대 C++ 라이브러리는 클래스를 중심으로 구성되어 있으므로, 라이브러리 튜토리얼을 살펴보는 것도 좋은 학습 방법입니다.

> ### <a name="Rbpi-6"></a>객체지향(OO)이 왜 그렇게 중요한가요?

클래스와 가상 함수를 활용한 객체 지향(Object-oriented) 기술은 대규모 복잡한 소프트웨어 시스템을 개발하는 중요한 방법 중 하나입니다. 또한 템플릿을 활용한 일반화(generic) 프로그래밍도 마찬가지로 중요한 기법입니다. 이 두 가지 방식은 각각 런타임과 컴파일타임에서 다형성(polymorphism)을 표현하는 강력한 수단이며, C++에서는 이 두 개념이 조화를 이루며 함께 작동합니다.

"객체지향", "객체지향 프로그래밍", 그리고 "객체지향 프로그래밍 언어"에 대한 정의는 매우 다양합니다. Bjarne Stroustrup가 생각하는 객체 지향이 무엇인지 더 자세히 알고 싶다면, "[Why C++ isn’t just an object-oriented programming language](https://www.stroustrup.com/oopsla.pdf)를 참고하세요. 그렇다면 객체지향 프로그래밍이란 무엇일까요? OOP는 약 40년 전 Simula에서 시작된 프로그래밍 스타일로, "캡슐화(encapsulation)", "상속(inheritance)", "다형성(polymorphism)"을 기반으로 합니다. C++을 포함한 많은 언어에서는 이를 클래스 계층(class hierarchy)과 가상 함수(virtual function)를 활용하여 구현합니다. 이러한 방식을 사용하면 다양한 객체를 공통된 인터페이스로 다룰 수 있으며, 기존 코드를 쉽게 확장할 수 있습니다.

객체지향의 핵심이 클래스라면, 클래스의 계층 구조를 만드는 이유는 무엇일까요?! 클래스를 계층적으로 구성하는 이유는 클래스 간의 관계를 명확히 표현하고, 코드의 복잡성을 줄이기 위함입니다. 객체 지향의 장점이 궁금하다면, [클래스(Class)의 장점은 무엇인가요?](#Rbpi-5)를 참고하면 도움이 될 것입니다.

객체 지향 프로그래밍을 제대로 이해하려면, 예제를 살펴보는 것이 가장 좋습니다. 예를 들어, 공통된 인터페이스를 가진 두 개 이상의 장치 드라이버를 생각해 봅시다. 우선 모든 Driver가 따라야 할 공통 인터페이스를 정의합니다.

```cpp
class Driver {  // 공통 드라이버 인터페이스
public:
    virtual int read(char* p, int n) = 0; // 장치에서 최대 n개의 문자를 p에 읽어오기
                                          // 읽어온 문자의 개수를 반환
    virtual bool reset() = 0;             // 장치 초기화
    virtual Status check() = 0;           // 상태 확인
};
```

이 Driver 클래스는 인터페이스(interface) 역할만 합니다. 데이터가 멤버가 없고 모든 함수가 순수 가상 함수로 선언되어 있습니다. 즉, Driver 자체로는 객체를 만들 수 없으며, 이 인터페이스를 구현하는 구체적인 드라이버 클래스를 통해서만 사용될 수 있습니다. 이제 Driver 인터페이스를 상속받아 실제 드라이버를 구현해 봅시다.

```cpp
class Driver1 : public Driver { // 첫 번째 드라이버
public:
    Driver1(Register);          // 생성자
    int read(char*, int n) override;    
    bool reset() override;
    Status check() override;
private:
    // 구체적인 구현(데이터, 내부 동작 등)
};
class Driver2 : public Driver { // 두 번째 드라이버
public:
    Driver2(Register);
    int read(char*, int n) override;    
    bool reset() override;
    Status check() override;
private:
    // 구체적인 구현(데이터, 내부 동작 등)
};
```

이 드라이버 클래스들은 자신만의 데이터(상태)를 저장하며, 이를 기반으로 객체를 생성할 수 있습니다. 각 드라이버는 Driver 인터페이스에서 정의한 기능들을 구현하고 있으며, 이를 활용하면 다음과 같이 사용할 수 있습니다.  

```cpp
void f(Driver& d)               // 드라이버 사용
{
    Status old_status = d.check();  
    // ...
    d.reset();
    char buf[512];
    int x = d.read(buf,512);
    // ...
}
```

여기서 중요한 점은, f() 함수는 어떤 종류의 드라이버가 전달되는지 전혀 신경 쓰지 않는다는 것입니다. 그저 Driver 인터페이스만 알면 되며, 이를 통해 다양한 종류의 드라이버를 동일한 방식으로 사용할 수 있습니다. f() 함수를 다음과 같이 사용할 수 있습니다.

```cpp
void g()
{
    Driver1 d1(Register(0xf00));  // 주소 0xf00에 있는 장치용 Driver1 생성
    Driver2 d2(Register(0xa00));  // 주소 0xa00에 있는 장치용 Driver2 생성

    int dev;
    cin >> dev;
    if (dev == 1) 
        f(d1);  // Driver1 사용
    else
        f(d2);  // Driver2 사용
}
```

위 코드에서 f(d1)을 호출하면 Driver1::read()가 호출되고, f(d2)을 호출하면 Driver2::read()가 호출됩니다. 이처럼, 함수 f()는 어떤 드라이버 객체가 전달되는지 몰라도 해당 객체에 맞는 동작이 자동으로 실행됩니다. 이런 동작 방식을 "런타임 디스패치(run-time dispatch)" 또는 "동적 디스패치(dynamic dispatch)"라고 부릅니다.

객체지향 프로그래밍(OOP)이 만능 해결책(panacea)은 아니라는 점을 명심해야 합니다. "OOP"가 곧 "좋은 코드"를 의미하는 것은 아닙니다. 문제의 본질적인 개념들 사이에 계층적인 관계(hierarchical relationships)가 없다면, 아무리 클래스 계층과 가상 함수를 사용한다고 해도 코드가 더 좋아지지는 않습니다. OOP의 강점은 클래스 계층을 통해 효과적으로 표현할 수 있는 문제들이 많다는 점입니다. 하지만 OOP의 단점은 너무 많은 사람들이 모든 문제를 억지로 계층적 구조로 해결하려 한다는 점입니다. 즉, 모든 프로그램이 객체지향 방식으로 설계될 필요는 없습니다. 대안으로는 다음과 같은 방법도 고려해 볼 수 있습니다.
* 단순한 클래스(Pain Classes)
* 일반화 프로그래밍(Generic Programming)(템플릿을 활용한 코드 재사용)
* 독립적인 함수(Free-standing Functions)(수학적 함수, C 및 Fortan 스타일의 프로그래밍)

여전히 "왜 객체지향을 써야 할까?"라는 의문이 든다면,  
기술적인 이유뿐만 아니라 비즈니스적인 이유도 고려해 볼 필요가 있습니다.  

소프트웨어 산업은 과거 수작업으로 이루어지던 많은 기능을 자동화하는 데 성공해 왔습니다. 뿐만 아니라, 기존의 기계 장치들이 점점 더 소프트웨어 기반으로 변화하고 있습니다. 예를 들어,  

* 기계식 장치 → 소프트웨어 기반 장치
    * 시계, 자동차 점화 시스템 등 많은 기계 장치가 소프트웨어로 대체
* 전기 회로로 작동하던 장치 → 소프트웨어 제어 장치
    * TV, 주방 가전제품 등도 점점 더 소프트웨어 기반으로 동작

그리고 이제 소프트웨어는 비즈니스의 모든 영역에 깊숙이 통합되고 있습니다. 초기에는 회계(Accounting)와 재무(Finance) 분야에서만 사용되었지만, 이제는 운영(Operations), 마케팅(Marketing), 영업(Sales), 경영(Management) 등 비즈니스의 거의 모든 분야에서 소프트웨어가 필수적인 요소가 되었습니다.

이러한 엄청난 성공은 소프트웨어 개발 조직이 그 속도를 따라잡는 능력을 지속적으로 시험해 왔습니다. 소프트웨어 산업은 대규모, 복잡한 소프트웨어 시스템에 대한 수요를 충족하는 데 지속적으로 실패해 왔습니다. 하지만 아이러니하게도, 이런 실패는 사실 소프트웨어가 제공하는 가치가 엄청나게 크기 때문입니다. 즉, 소프트웨어에 대한 수요가 우리가 감당할 수 있는 공급을 초과했기 때문에 이런 문제가 발생한 것입니다. 소프트웨어 업계에서는 이러한 수요를 자축할 수도 있겠지만, 혁신가와 리더는 결코 현재에 만족하지 않는다는 특징을 가지고 있습니다. 우리는 더 잘해야 합니다. 그것도 훨씬 더. 말 그대로 엄청나게(Uber better) 더 잘해야 합니다.

과거의 성공은 사용자들의 기대치를 높였고, 그 결과 기존의 구조적 분석(Structured Analysis), 설계(Design), 프로그래밍 기법으로는 이러한 요구를 충족할 수 없었습니다. 이 때문에 우리는 더 나은 패러다임이 필요했고, 실제로 여러 개의 새로운 패러다임이 등장했습니다.

C++는 객체지향 프로그래밍(OOP)을 지원하지만, 단순히 객체지향 언어로만 사용해야 하는 것은 아닙니다. C++는 다음과 같은 다양한 스타일로 사용할 수 있습니다.
1. 전통적인 명령형 프로그래밍(Imperative Programming)
   * C++를 "더 나은 C"로 사용 가능
2. 제네릭 프로그래밍(Generic Programming)
   * 템플릿을 활용한 유연한 코드 작성
3. 객체지향 프로그래밍(Object-Oriented Programming, OOP)
   * 클래스와 가상 함수를 통한 계층적 설계
4. 함수형 프로그래밍(Functional Programming, FP)
   * 최근에는 C++도 함수형 프로그래밍을 적극 지원하기 시작

각 접근 방식은 장점과 단점이 있으며, 하나의 스타일을 사용하면서 다른 스타일의 이점을 기대해서는 안 됩니다. (가장 흔한 오해: C++를 단순히 "더 나은 C"로 사용하면서 OOP의 이점을 기대하는 것)

훌륭한 프로그래머는 특정한 프로그래밍 스타일에 집착하지 않습니다. 즉, "내가 좋아하는 방식"을 모든 문제에 억지로 적용하는 것은 바람직하지 않습니다. 대신, 상황에 맞는 최적의 접근법을 선택할 줄 알아야 합니다.
* 어떤 문제는 OOP로 해결하는 것이 좋을 수도 있고,
* 어떤 문제는 제네릭 프로그래밍이 더 적합할 수도 있으며,
* 때로는 함수형 프로그래밍 기법이 더 효과적일 수도 있습니다.

더 나아가, 가장 좋은 해결책은 OOP, 제네릭, 함수형 프로그래밍을 조합하는 것일 수도 있습니다. 반대로, 하나의 특정한 패러다임에만 의존하면 비효율적인(suboptimal) 해결책이 될 가능성이 높습니다.

> ### <a name="Rbpi-7"></a> What’s the big deal with generic programming?

### What is multiparadigm programming?

### Is C++ better than Java? (or C#, C, Objective-C, JavaScript, Ruby, Perl, PHP, Haskell, FORTRAN, Pascal, Ada, Smalltalk, or any other language?)

### Why is C++ so big?

### Who uses C++?

### How long does it take to learn C++?

### What’s the best way to improve my C++ programs?

### Does it matter which programming language I use?

### What are some features of C++ from a business perspective?

### Are virtual functions (dynamic binding) central to OO/C++?

### I’m from Missouri. Can you give me a simple reason why virtual functions (dynamic binding, dynamic polymorphism) and templates (static polymorphism) make a big difference?

### Is C++ backward compatible with ANSI/ISO C?

### Why is C++ (almost) compatible with C?

### When was C++ invented?

### Why was C++ invented?

### Where did the name C++ come from?

### Why does C++ allow unsafe code?

### Why are some things left undefined in C++?

### Why is portability considered so important?

### Is C++ standardized?

### Who is on the standardization committee?

### Where can I get a copy of the C++ standard?

### What is the difference between C++98 and C++03?

### What is the difference between C++98 and C++0x?

### What is the difference between C++98 and C++11?

### What is the difference between C++11 and C++14?

### What are some “interview questions” I could ask that would let me know if candidates really know their stuff?

### What does the FAQ mean by “such and such is evil”?

### Will I sometimes use any so-called “evil” constructs?

### Is it important to know the technical definition of “good OO”? Of “good class design”?

### What should I tell people who complain that the word “FAQ” is misleading, that it emphasizes the questions rather than the answers, and that we should all start using a different acronym?
