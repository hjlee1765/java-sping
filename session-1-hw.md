SPRING
======

SPRING 을 학습하고 기록합니다.

## 1. JVM
Java Byte Code(.calss)를 OS에 상관없이 실행하게 해준다.

### 1.1 Class Loader
    Java Byte Code(.class)를 Runtime 시에 동적으로 메모리에 올려준다.

쉽게 말하면, Class A = new HelloWorld(); 라는 코드를 실행할 때, Class Loader가 HelloWorld를 메모리에 로드한다.

### 1.2 Hierarchical
Class Loader는 계층적 구조를 갖게된다. Class Loading 요청을 받을 때, 최상위 Parent가 우선권을 가지고 있고, 요청받은 class가 없으면 아래 Class Loader로 내린다. (**Delegate Load Request**)

* #### Bootstrap Class Loader
    JVM이 실행될 때 맨 처음 실행되는 최상위 클래스 로더.
    ($JAVA_HOME/jre/lib/rt.jar)에 있는 클래스를 로딩한다.

* #### Extensions Class Loader
    Bootstrap Loading 후 기본적으로 로딩되는 클래스.
    ($JAVA_HOME/lib/ext/*.jar)에 있는 확장 클래스들이 로딩한다

* #### System Class Loader
    Class path 환경변수에 의해 설정된 경로에서 클래스를 로딩한다.

* #### User-Defined Class Loader
    Application에서 사용자가 직접 코드 상에서 생성해서 사용하는 클래스 로더이다.

## 2. WAS
OS > JVM > WAS 안에, 여러 WebApplication을 등록할 수 있는데, **context path**로 구분한다.

원래 WebApplication은 WAS에 배포를 해서 실행시켜야 하는데, Spring boot는 WAS가 내장되어 있다.


## 3. AOP
Aspect-Oriented Programming: 관점 지향 프로그래밍

![My image](img/aop1.png "aop")

특정 기능이 있는 클래스 안에는 핵심적인 처리만 하고, 본질적이지 않은 기능들은 따로 기술.

핵심기능을 위한 코드보다 부가적인 기능(로그, 예외처리 등) 을 위한 코드가 많아지기에, Aspect라는 하나의 단위로 모아 기술한다.

* #### Join Point
    횡단 관심 모듈의 기능이 동작할 수 있는 특정 위치.

* #### Point cut
    어떤 클래스의 어느 Join Point를 사용할 것인지 결정하는 선택 기능.

* #### Advice
    각 Join Point에 삽입되어져 동작할 수 있는 코드

## 4. JAVA
자바 프로그램은 한 개 이상의 클래스 조합으로 실행된다. 실행 시 모든 클래스 파일이 JVM 메모리에 로딩되지 않고 요청되는 순간 로딩된다.

```
1. 컴파일 타임 환경
    .java -> 컴파일러 -> .class
2. 런타임 환경
    .class -> Class Loader -> JVM
```

### 4.1 Singleton
자바의 디자인패턴. 클래스의 인스턴스가 하나만 만들어지고, 어디서든지 그 인스턴스에 접근할 수 있도록 하기 위한 패턴.

* 생성자 -> private
* 최초 getInstance 호출시, 객체 생성. 그 후로는 만들어진 객체인 one을 리턴.

``` Java
    class Singleton {
        private static Singleton one;
        private Singleton() {
        }

        public static Singleton getInstance() {
            if(one==null) {}
                one = new Singleton();
            }
            return one;
        }
    }

    public class SingletonTest {
        public static void main(String[] args) {
            Singleton singleton1 = Singleton.getInstance();
            Singleton singleton2 = Singleton.getInstance();
            System.out.println(singleton1 == singleton2);
        }
    }
```


### 4.2 Thread와 공용객체
하나의 객체를 여러개의 쓰레드가 사용한다는 것을 의미.

## 5. Build Tool

### 5.1 Maven
* 라이브러리 관리 (pom.xml)
* 프로젝트 라이프 사이클 관리 : 빌드순서 complie -> test-> package

### 5.2 Gradle
* Ant + Maven의 장점
* xml 대신 Groovy문법을 사용.




