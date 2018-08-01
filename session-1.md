SPRING
======

SPRING 을 학습하고 기록합니다.

# JAVA 프로그램
자바 프로그램은 한 개 이상의 클래스 조합으로 실행된다. 실행 시 모든 클래스 파일이 JVM 메모리에 로딩되지 않고 요청되는 순간 로딩된다.

```
1. 컴파일 타임 환경
    .java -> 컴파일러 -> .class
2. 런타임 환경
    .class -> Class Loader -> JVM
```

## 1. JVM
---------
Java Byte Code(.calss)를 OS에 상관없이 실행하게 해준다.

### 1.1 Class Loader
> Java Byte Code(.class)를 Runtime 시에 동적으로 메모리에 올려준다.

 쉽게 말하면, Class A = new HelloWorld(); 라는 코드를 실행할 때, Class Loader가 HelloWorld를 메모리에 로드한다.

### 1.2 Hierarchical
Class Loader는 계층적 구조를 갖게된다. Class Loading 요청을 받을 때, 최상위 Parent가 우선권을 가지고 있고, 요청받은 class가 없으면 아래 Class Loader로 내린다.

이를 **Delegate Load Request**라 한다.


#### Bootstrap Class Loader
JVM이 실행될 때 맨 처음 실행되는 최상위 클래스 로더.
($JAVA_HOME/jre/lib/rt.jar)에 있는 클래스를 로딩한다.

#### Extensions Class Loader
Bootstrap Loading 후 기본적으로 로딩되는 클래스.
($JAVA_HOME/lib/ext/*.jar)에 있는 확장 클래스들이 로딩된다. 

#### System Class Loader
Class path 환경변수에 의해 설정된 경로에서 클래스를 로드한다.

##### User-Defined Class Loader
Application에서 사용자가 직접 코드 상에서 생성해서 사용하는 클래스 로더이다.

#### 1.3 WAS
OS > JVM > WAS 안에, 여러 WebApplication을 등록할 수 있는데, **context path**로 구분한다.

원래 WebApplication은 WAS에 배포를 해서 실행시켜야 하는데, Spring boot는 WAS가 내장되어 있다.


### 2 AOP
---------

