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



