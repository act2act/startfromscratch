# Cpp Syntax
## 들어가기전에 Markdown 문법
- 헤더: '#'의 개수로 제목의 수준을 표현
- 강조: * * 또는 _ _로 이탤릭체를, ** ** 또는 __ __로 볼드체를 표현
- 목록: '-'나 '*'로 순서 없는 목록을 표현
- 링크: [Link text]'(URL)로 링크를 추가
- 이미지: ![Alt text]'(URL)로 이미지를 추가
- 인라인 코드: 벡틱(``)을 사용해서 작성
- 코드 블록: 벡틱을 세번(``````) 사용해서 작성

## Git update
1. 변경사항 확인: git status로 현재 변경된 사항을 확인
2. 변경사항 추가: git add . 또는 특정 파일을 지정해서 스테이징 영역에 추가
3. 커밋 생성: git commit -m "commit message"로 변경사항에 대한 커밋을 생성
4. 브랜치 확인: git branch로 현재 작업중인 브랜치를 확인
5. git push origin branch로 변경사항을 원격 저장소에 푸시

## C++의 특징
- **객체지향형 프로그래밍(OOP)**: 클래스와 객체를 지원하며 상속성, 다형성, 캡슐화 같은 핵심 개념을 완벽히 지원한다.
- **절차적 프로그래밍**: C의 후속 언어로 절차적 프로그래밍의 특징도 그대로 유지하고 있다. 함수를 사용한 코드 모듈화가 가능하며, 복잡한 문제를 작은 문제로 나누어 문제 해결을 할 수 있다.
- **저수준 접근 가능성**: 메모리 접근, 비트 단위 연산 등 저수준 컴퓨팅 작업을 직접 제어할 수 있는 기능을 제공한다.
- **STL(Standard Template Library)**: STL은 다양한 프로그래밍 데이터 구조(예: 벡터, 리스트, 맵)와 알고리즘(예: 정렬, 검색)을 제공한다.
- **메모리 관리의 유연성**: C++에서는 new와 delete 연산자를 이용해 동적 메모리 할당과 해제를 직접 제어할 수 있다.

## 기본 구조
```
#include <iostream>

int main(
    std::cout << "Hello." << std::endl;

    return EXIT_SUCCESS;
)
```

- `#include`: 외부 헤더파일을 추가하는 전처리자(preprocessor)  
- `<iostream>`: 표준 라이브러리 헤더 파일  
- `int main(int argc, char* argv[])`: 모든 프로그램의 진입점인 main 함수와 매개변수 
- `std::cout`: 템플릿 클래스로 구현된 출력스트림의 전역 객체  
- `using std::cout`: namespace 내의 내용을 접근자 없이 사용  
- `"Hello."`: 문자열 리터럴
- `;`: 하나의 문장을 끝마치는 문자   
- `return`: 함수의 반환값 처리  
- `EXIT_SUCCESS`: 값이 0인 매크로

## 변수
변수는 `하나의 값을 저장할 수 있는 공간`으로 해석한다. 변수 선언은 컴파일러에게 변수의 속성에 대한 세부 정보를 제공하는 것이다.  
변수 이름은 사람을 위한 것으로 컴파일 후 실행 프로그램에서 변수명은 없고 메모리 공간에 저장된 값과 명령만 존재한다.

### 선언과 정의
```
extern int Number; /// extern은 전역으로 int형 자료 Number가 어디선가 정의 될 것이라고 "선언"

int nCount; /// int형 자료를 저장할 수 있는 nCount 변수(메모리 공간)를 "정의"
```
### 초기화
초기화는 정의된 자료형의 메모리 공간에 값을 설정하는 것이다.
```
int n = 10;
```
### 대입
대입은 변수 정의로 만들어진 메모리 공간에 값을 설정하는 것이다.
```
int n;
a = 10;
```

### 데이터 타입과 크기
```
bool b = true // 불리언형, 1 byte

char a = "string"; // 문자형, 1 byte

wchar_t // wide character, 4 byte

int n = 10; // 정수형, 4 byte, 32/64bit 시스템 상관없다.

long l = 0; // 정수형, 8 byte, 64bit 시스템

float m = 0.F; // 실수형, 4 byte

double d = 0.; // 실수형, 8 byte, float보다 더 큰 범위의 실수를 사용할 수 있어 정밀도가 더 높다.

void // 데이터를 저장하는 데 사용되지 않고, 주로 함수에서 반환 값이 없을 때 사용되는 반환 타입으로 활용된다.
```

### 메모리 관리
메모리 관리는 프로그램이 실행되는 동안 사용할 수 있는 메모리 공간을 할당, 사용, 해제하는 과정을 말한다. 효율적인 관리는 프로그램의 성능과 안정성에 영향을 끼친다.  
- **동적 메모리 할당**: 프로그램 실행 중 메모리 공간을 할당
```
int* ptr = new int; // 동적으로 int 크기의 메모리 할당
*ptr = 5; // 할당된 메모리에 값 저장
```
- **메모리 누수 방지**: 할당된 메모리를 적절히 해제하여 사용하지 않는 메모리가 시스템에 남아 있지 않도록 관리
```
int* ptr = new int[10]; // 동적으로 int 배열 할당
delete[] ptr; // 배열 사용 후 메모리 해제하여 누수 방지
```
- **가비지 컬렉션**: 자동으로 메모리 누수를 감지하고 해제하는 기능으로 C++ 표준에는 포함되어 있지 않지만, 스마트 포인터를 사용해 비슷하게 구현할 수 있다.
```
#include <memory>

std::unique_ptr<int> ptr = std::make_unique<int>(5); // 동적 할당과 자동 메모리 관리
```

### 포인터 변수
포인터는 메모리 주소를 저장하는 변수로, C++에서 메모리의 직접적인 접근과 조작을 가능하게 하는 기능이다. 이를 통해 단순히 변수에 접근하는 것보다 데이터 구조를 더 유연하게 다룰 수 있다.
```
int main() {
    int var = 20; // 실제 변수 선언
    int *ip; // 포인터 변수 선언

    ip = &var; // var 주소를 포인터 변수에 저장

    /*
    선언과 동시에 초기화하는 방법    
    int var = 20;
    int *ip = &var;
    */

    std::cout << var << std::endl; // 20
    std::cout << *ip << std::endl; // 20

    return 0;
}
```

### 상수
const는 언제든 변할 수 있는 객체를 불변으로 정의하는 예약어다.
```
const int n;

int const n;

위 두 개는 변수를 상수로 만들어서 값을 변경할 수 없게 한다는 의미에서 동일하다.
```

### 정적 변수와 동적 변수
- **정적 변수**: 프로그램이 실행, 생성되고 종료될 때까지 메모리에 남아있는 변수이다. 만약 함수 내에서 정적 변수를 선언했다면 전체 프로그램이 종료되지 않는 한 그 함수가 종료되어도 값이 사라지지 않는다.
- **동적 변수**: 프로그램 실행 중에, 특히 런타임에 메모리를 할당받아 생성되는 변수이다. 사용이 끝난 후에는 개발자가 직접 메모리를 해제해야 한다.

### 범위와 수명
- **범위**: 변수가 프로그램 내에서 접근 가능한 영역을 말한다. 예를 들어, 지역 변수는 선언된 함수 내에서만 접근할 수 있고 전역 변수는 프로그램 전체 어디서나 접근 가능하다.
- **수명**: 변수가 메모리에 할당되어 있는 기간을 말한다. 예를 들어, 지역 변수의 수명은 함수 호출부터 함수 실행이 종료되면 끝나고 전역 변수나 정적 변수의 수명은 프로그램이 실행되고 끝날 때까지 지속된다. 동적 변수의 수명은 개발자가 메모리를 할당하고 해제하는 시점에 따라 결정된다.

## 조건문과 반복문
### 조건문
조건이 성립하는 경우에만 소스코드를 수행하도록 하는 명령어이다.
```
if (a > 5)
{
    std::cout << "a is bigger than 5";
}
else
{
    std::cout << "a is not bigger than 5;
}
```
### 반복문
프로그램 내에서 똑같은 명령을 특정 횟수만큼 반복하여 수행하도록 하는 명령어이다.
```
for (int i=0; i<5; i++)
{
    std::cout << i; // 0 1 2 3 4
}
```

## 함수
함수는 특정한 목적을 위해 독립적으로 쓰인 코드의 집합이다.

#### Call by value
함수에 인자를 전달할 때 그 값의 복사본을 생성하여 전달하는 방식을 말한다. 함수 내에서 인자의 값이 변경되어도 외부의 변수에는 영향을 주지 않는 중요한 특성이다.
```
int add(int a, int b)
{
    // 2. 넘겨받은 복사본으로 계산을 한다.
    return a + b;
}

int main()
{
    int a = 1;
    int b = 2; // 3. 따라서 기존 a, b에는 영향을 끼치지 않는다.
    int sum = add(a, b); // 1. a, b의 복사본을 넘겨준다.

    std::cout << sum; // 3
}
```
리턴 값이 없는 함수도 가능하다.
```
void print()
{
    std::cout << "Hi!";
}
```
## 구조체
구조체(Structure)는 여러 데이터 항목을 하나의 단위로 묶어서 다루기 위한 C++ 기본 데이터 타입 중 하나이다.  

#### 클래스와 차이점은 무엇인가?
클래스가 데이터와 그 데이터를 다루는 함수를 모두 포함할 수 있는 반면, 전통적인 구조체는 데이터 항목만 포함한다. 하지만 C++에선 구조체도 함수를 가질 수 있어서 클래스와 매우 유사하다. 구조체의 멤버는 기본적으로 public이고, 클래스의 멤버는 기본적으로 private이라는 차이점이 있다.

```
#include <iostream>
#include <string>

struct Player
{
    int hp = 1;
    std::string name = "name1";
}

int main() {
    Player p1;
    std::cout << p1.hp; // 1
    std::cout << p1.name; // name1
}

```


## 클래스와 객체
클래스는 붕어빵을 만드는 틀이고 객체는 그 틀에서 찍혀나오는 각각의 붕어빵(인스턴스)이다. 이것들은 팥 붕어빵이고 사람처럼 먹거나 말할 수 있다고 가정해보자.
```
class Bread
{
    private:
        string filling = "red bean";

    public:
        void eat(){
            std::cout << "Eating";
            }

        void talk(){
            std::cout << "Talking";
        }
}
```
Private과 Public을 구분해준 이유는 객체지향적 속성 중 *캡슐화* 때문이다. 자세한건 아래에서 살펴보자.
## 객체지향적 프로그래밍(OOP)
실세계의 사물을 객체로 모델링하여 프로그램을 구성하는 방법론이다. 이를 통해 복잡한 시스템을 보다 쉽게 관리하고 이해할 수 있게 만든다.
#### 핵심개념
1. **상속성(inheritance)**: 코드의 재사용을 통해 새로운 기능을 쉽게 추가할 수 있게 한다.
```
class Vehicle {
    public:
        void move() {
            std::cout << "Vehicle is moving"
        }
};

class Car : public Vehicle {
    public:
        void move() {
            std::cout << "Car is moving"
        }
}
```
2. **다형성(polymorphism)**: 같은 인터페이스 아래에서 다른 행동을 구현할 수 있게 하여 코드의 유연성을 높인다.
```
Vehicle* v = new Car();
v->move(); // Car is moving
```
3. **캡슐화(encapsulation)**: 객체의 세부 구현을 숨기고 필요한 부분만 노출시켜 데이터 보호와 인터페이스 간소화를 할 수 있다.
```
class Vehicle {
    private:
        int speed;

    public:
        void setSpeed(int s) {
            speed = s;
        }

        int getSpeed() {
            return speed;
        }
}
```
## 예외 처리
프로그램 실행 중 예외가 발생할 경우, try 블록 내의 코드 실행이 중단되고, 해당 예외를 처리할 수 있는 catch 블록으로 제어가 이동한다. 이를 통해 예외 상황에서도 안정적으로 동작하도록 관리할 수 있다.
```
try {
    throw "An error occured";
}
catch(const char* msg) {
    std::cout << msg;
}
```

#### 주요 예외 유형
std::exception 파생 클래스들
- std::runtime_error: 실행 시간 오류
- std::logic_error: 프로그램 로직 오류
- std::out_of_range: 범위를 벗어난 접근 시
- std::invalid_argument: 잘못된 인자 전달 시
```
#include <iostream>
#include <stdexcept> // 표준 예외 클래스 사용을 위한 헤더

int main() {
    try {
        // error code
        throw std::out_of_range("Index out of range");
    }
    catch(const std::exception& e) {
        std::cout << e.what(); // what()은 발생한 예외의 설명을 반환한다.
    }
}
```