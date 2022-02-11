# TIL
## 1강 스프링 개념 잡기
### 스프링이란?
1. FrameWork
    틀(Frame)과 동작(work), 이 틀 안에서 동작한다는 뜻
2. 오픈 소스이다
    - 공개된 소스코드, 즉 내부를 뜯어 고칠 수 있다는 뜻
3. IOC 컨테이너를 가진다
    IOC 컨테이너란?
    - 스프링의 핵심이다
    - (Inversion Of Controll) : 역전의 제어, 주도권이 스프링에 있다
        - Class → 설계도
        - Object → 실체화가 가능한 것
            #####       ex: 
        - Instance → 실체화가 된 것
    - Object를 new를 통해 heap 메모리 공간에 올릴 수 있다.
        <br> 의자 s = new 의자(); 선언한 레퍼런스 변수는 public void make() {} 내부에서 관리한다.
        하지만 메소드를 실행할 때 그 당시에만 메모리 영역에 올라가기 때문에 다른 메서드에서 동일한 변수를 선언해도 같은 주소 값을 가지지 않기 때문에 새로운 공간이 생겨나게 된다.
    - 스프링에서는 많은 Object들을 한 번만 선언해도 동일한 주소 값을 가지게 하여 직접 스프링에서 할당한다. 그것을 가능하게 하는 게 IoC이다.
4. DI를 지원한다.
    - D(Dependency)I(Injection)란?
        - Object를 스프링에서 관리하기 때문에 같은 주소 값을 가진 변수를 사용할 수 있으며 싱글톤이라고 한다.
        - 객체를 필요한 부분에서 가져와 사용하는 것이다.

## 2강 스프링 개념 정리
### 필터란 무엇인가요?
1. 문지기: 걸러내라는 임무 부여
    - 검열의 기능을 해 주는 것
    - 특정한 권한을 가진 것만 접근 가능
2. 필터의 종류
    - 스프링 자체에 필터 기능 있으며
    - 필터가 비활성화된 것을 활성화시켜 사용할 수 있고
    - 직접 필터를 생성할 수 있다
3. 보통 톰캣에서 사용하는 필터는 filter라고 불리며 web.xml에서부터 실행되지만 스프링 컨테이너에서 실행되는 필터는 인터셉터(AOP)라고 불린다. 인터셉터는 필터와 비슷하며 권한을 체크한다.
### 어노테이션이란 무엇인가요?
1. 주석과 힌트가 합쳐진 것이다.
    - 보통 // 글 ~ (주석) 처리된 것은 컴파일러가 무시하기 때문에 기능이 실행되지 않지만, 어노테이션이 들어간 주석은 컴파일러가 무시하지 않고 기능을 실행시킨다.

    - 스프링에서는 어노테이션 사용시 객체를 생성한다.

    @Component → 클래스 메모리에 로딩 (HEAP 메모리 영역에 할당)<br>
    @Autowired → 로딩된 객체를 해당 변수에 집어넣음

    런타임을 싱행하면 해당하는 class를 실행시키는데 이때 메소드, 필드, 어노테이션 등을 분석하는 것을 리플렉션이라고 한다. 스캔하며 체킹을 하면 설정이 되는 것.

## 3강 스프링 개념 정리
### 메시지 컨버터가 무엇인가요?
1. Message Converter의 기본 값는 Json이다.
    - 영어권과 한국권에서 서로 각자의 언어로 말을 하면 그 언어를 알지 못한다고 가정했을 때 서로 이해 불가하다. 그렇게 각자 다른 언어 프로그래밍을 사용한다면 소통 불가함 → 그래서 모든 나라에서 사용할 수 있는 중간 언어가 필요

    
    Java → Json → python<br>
    Java ← Json ← python

2. Json은 요청할 때도 사용되지만 상대한테 응답받을 때에도 사용된다.
    
    - 자바 프로그램  →  Json (request: 요청) MessageConverter 작동  →  파이썬 프로그램<br>
    자바 프로그램  ←  Json (response: 응답) MessageConverter 작동 ←  파이썬 프로그램

### BufferedReader, BufferedWriter란 무엇인가요?
1. 처음 영어권에서 통신을 사용할 때 bit단위로 사용하면 소통이 어렵다는 것을 알게 되어 8bit씩 끊어 읽는 byte를 개발하였다. 1byte는 8bit트를 나타내며 byte는 논리적으로 부르는 것이고 현재의 통신 단위이다. 하지만 여러 나라에서는 서로 다른 언어를 사용하기 때문에 이를 지원할 수 있는 유니코드의 UTF-8(3BTYE 통신)이 등장한다.
2. 데이터를 보낼 때 ByteStream으로 1Byte(8bit) 자바 프로그램에서 읽어들일 때 InputStram으로 읽어내는데 InputStream으로 읽으면 바이트 통신을 하기 때문에 문자(char)로 casting을 해야 하는 등 복잡하기 때문에 InputStreamReader라는 클래스로 감싸서 byte를 문자 하나로 변경해 준다. 이때 배열로 여러 개의 문자를 받는데 배열의 단점이 있다. 크기가 정해져 있어야 하기 때문에 MAX 크기로 설정해 둔다면 작은 데이터를 사용할 때 낭비할 수 있기 때문이다.

그래서 나온 클래스가 BufferedReader와 BufferedWriter이다. 이 클래스는 가변 길이의 문자를 받아 준다.<br><br>
    1. 요청해서 데이터를 받을 때 BufferedReader, JSP에서는 request.getReader
    2. 데이터 응답할 때에는 BufferedWriter가 아닌 PrintWriter 사용, print() 함수와 println() 함수를 제공 -> BufferedWriter는 내려쓰기 기능이 없기 때문, JSP에서는 내장객체 out(out 자체가 BufferedWriter)을 사용한다

직접 구현하지 않고 제공하는 어노테이션: <br>@ResponseBody(BufferedWriter 기능), @RequestBody(BufferedReader 기능)


## 4강 스프링 개념 정리
### JPA란?
1. Java Persistence Application Programing interface이다.
    - 자바 데이터를 영속성으로 기록할 수 있는 환경을 뜻한다.
    - API란? - 애플리케이션 프로그래밍 인터페이스를 뜻하는데, 이는 인터페이스로 프로그래밍한 프로그램이라고 한다. 인터페이스는 상하관계가 존재하는 약속이라는 개념을 가지고 있으며, 이와 상반되는 건 프로토콜 개념이다. 프로토콜은 상하관계 없이 권리가 동등하다.

## 5강 스프링 개념 정리
### ORM이란 무엇인가요?
ORM(Object Relational Mapping)
<br><br>1. Class를 만들 때 model class라는 것이 있음, 모델링이란 추상적인 개념이며 현실세계를 뽑아 내는 것이다
  - 기본적으로 데이터베이스의 테이블과 자바의 class는 타입이 다르기 때문에 모델링을 해 줘야 한다. DB 세상에 있는 데이터를 JAVA 세상에 모델링을 하는 것을 TRM(Table Relational Mapping)이라고 하며, 이것이 역전된 게 ORM(Object Relational Mapping)이다. 즉, JAVA 세상에 있는 데이터를 DB로 전송할 때 데이터 타입을 바꿔 주는 것이다.
  - JAVA에서 Class를 먼저 만든 후 데이터베이스에 자동 생성을 하려면 JPA의 인터페이스가 필요하다.
<br><br>
2. 반복적인 CRUD 작업을 생략하게 해 준다.
    - INSERT             : INSERT <B>C</B>REATE
    - SELECT, SELECT ALL : <B>R</B>EAD
    - UPDATE             : <B>U</B>PDATE
    - DELETE             : <B>D</B>ELETE
<BR>

        - 자바에서 DB로 Connection 요청 → DB가 Session 오픈 → 자바는 Connection 가짐 → Query 전송 가능 → Query 전송시 데이터 응답 → 데이터 타입과 자바의 Object 타입이 다르기 때문에 타입 변경해 줘야 함 
<br>
    - 해당하는 단순한 반복 로직을 줄여 주는 것이 JPA이다. 즉, 전송된 Query에 대한 응답이 있을 때 데이터를 JAVA Object 타입으로 바꿔 주고 Connection을 끊는 단순한 반복 작업을 줄여 주는 것이다.
