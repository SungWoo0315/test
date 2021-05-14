```java
//package hello;
//공백: white space ( 줄바꿈, 스페이스, 탭...)
public class HelloJava {
	public static void main(String[] args) {
		System.out.println("Hello, Java");
		System.out.println("안녕, java");
	}
}
```




- 주석처리

한줄 //

영역 /* */

```java
/* package hello;
 공백: white space ( 줄바꿈, 스페이스, 탭...) */

public class HelloJava {
	public static void main(String[] args) {
		System.out.println("Hello, Java");
		System.out.println("안녕, java");
	}
}
```

----

```java
/* package hello;
 공백: white space ( 줄바꿈, 스페이스, 탭...) 
*/


public class HelloJava {
/*	public static void main(String[] args) {
		System.out.println("Hello, Java");
		System.out.println("안녕, java");
	} */
}
```

```cmd
C:\Users\kosmo>javac HelloJava.java

C:\Users\kosmo>java HelloJava
Error: Main method not found in class HelloJava, please define the main method as:
   public static void main(String[] args)
or a JavaFX application class must extend javafx.application.Application
```

클래스 안에
메인 메소드가 있어야 한다.

자바컴파일은 되지만 실행이 에러남 

메인 메소드가 없으면 Error 출력.

----


`;` 세미콜론 줄막음, 


`package` 들어갔을 경우

```cmd
C:\Users\kosmo>javac HelloJava.java

C:\Users\kosmo>java HelloJava
Error: Could not find or load main class HelloJava
Caused by: java.lang.NoClassDefFoundError: hello/HelloJava (wrong name: HelloJava)
```


찾을수 없는 것과 동일한 에러 

```cmd
C:\Users\kosmo>java HelloJava22
Error: Could not find or load main class HelloJava22
Caused by: java.lang.ClassNotFoundException: HelloJava22
```

클래스가 보이는데 에러, 가상머신이 인식못하도록 하는 `package` 서브디렉토리 형태로 숨김.

hello 폴더 밑에 HelloJava가 있다고 인식. 

위치를 제대로 알려줘야한다.  class path

#

컴파일할때 디렉토리 구조로 하는 법

```cmd
C:\Users\kosmo>javac -d . HelloJava.java
```

-d . 현재 디렉토리로 지시



> 소스 충돌 방지를 위해 쓰는것이 `package`

#

실행방법

```cmd
C:\Users\kosmo>java -cp . hello.HelloJava
Hello, Java
안녕, java
```

#
















