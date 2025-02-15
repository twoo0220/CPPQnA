# Big Picture Issues

## <a name="S-bpi"></a>Contents of this section\:

* [C++은 무엇입니까?](#Rbpi-1)
* [C++은 실용적인 언어입니까?](#Rbpi-2)
* [C++은 완벽한 언어입니까?](#Rbpi-3)
* [제로 오버헤드(Zero-overhead) 원칙이란 무엇인가요?](#Rbpi-4)
* [클래스(Class)의 장점은 무엇인가요?](#Rbpi-5)
* [객체지향(OO)이 왜 그렇게 중요한가요?](#Rbpi-6)

> ### <a name="Rbpi-1"></a>C++은 무엇입니까?

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
