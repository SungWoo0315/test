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


주석처리를 제거하고 `package`가 들어갔을 경우

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

----

## 실습

패키지 지정 실습

- 메모장에 소스코드 작성.

```java
package kosmo;

public class MyName {
	public static void main(String[] args) {
		System.out.println("내 이름은 Kosmo 입니다");
	}
}
```

#

- `cmd`에서 `javac`로 컴파일 후 `java`로 실행.

```cmd
C:\Users\kosmo>javac -d . MyName.java

C:\Users\kosmo>java -cp . kosmo.MyName
내 이름은 Kosmo 입니다

```

`C:\Users\kosmo` 밑에 `kosmo` 폴더가 생성되고 그 밑에 `MyName.class` 가 생성 됨.

올바르게 출력되는것을 볼 수 있다.

> -d : package에서 정한 디렉토리 생성  
> -cp : classpath 클래스 위치 지정
> `.` 현재디렉토리를 지시.

#

`C:\Users\kosmo>cd`

현재 디렉토리 위치 및 이동

```cmd
C:\Users\kosmo>cd "My Documents"

C:\Users\kosmo\My Documents>
```

다른 디렉토리에서 자바를 실행

`.` 현재 디렉토리를 지시. `..` 한단계 전 디렉토리를 지시.

```cmd
C:\Users\kosmo\My Documents>java -cp ..\
```

> kosmo 위치를 지칭
> 

```cmd
C:\Users\kosmo\My Documents>java -cp ..\ kosmo.MyName
내 이름은 Kosmo 입니다
```

#


- 절대경로

> 리눅스는 / (슬래시) 기반

> 윈도우는 디스크 기반 `C:`


```cmd
C:\Users\kosmo\My Documents>java -cp C:\Users\KOSMO kosmo.MyName
내 이름은 Kosmo 입니다
```

절대경로로 실행해도 잘 출력 됨.


#

## 커맨드라인

`dir`

`cd`

`.` 현재 위치

`..` 앞의 위치

`절대경로 dir c:\`


`md` make 디렉토리 (디렉토리 생성)    
= `mkdir`  
> `md /?` 사용법 보기  

```cmd
C:\Users\kosmo\My Documents>md /?
디렉터리를 만듭니다.

MKDIR [드라이브:]경로
MD [드라이브:]경로

명령 확장을 사용하면 MKDIR은 아래와 같이 바뀝니다.

필요한 경우 MKDIR은 경로 상에 중간 디렉터리를 만듭니다.
예를 들어, \a가 없다고 가정하면

    mkdir \a\b\c\d

는 확장을 사용하지 않는 경우의

    mkdir \a
    chdir \a
    mkdir b
    chdir b
    mkdir c
    chdir c
    mkdir d

와 같습니다.  
```

```cmd
C:\Users\kosmo\My Documents>md Sample\A\B\C
```

> Sample 만들고 그밑에 하위폴더 A B C 하위로 생성

> `md 폴더명` 단순 폴더 생성
> 

> `cd ..` 상위 폴더 이동.
> 


어러번 한꺼번에 이동

```cmd
C:\Users\kosmo\My Documents\sample\A\B\C>cd ..\..\..\..\

C:\Users\kosmo\My Documents>


절대경로 이동

C:\Users\kosmo\My Documents>cd "\Users\KOSMO\My Documents\sample\A\B\C"

C:\Users\kosmo\My Documents\sample\A\B\C>

```

> 도스는 대소문자 구문 없고, 파워쉘은 대소문자 구분 한다.

#

`del` `ERASE` 파일 삭제

```cmd
C:\Users\kosmo\Documents>del test
C:\Users\kosmo\Documents\test\*, 계속하시겠습니까(Y/N)? y
```

> `test` 폴더 내 파일을 전부 삭제한다는 의미. (폴더는 삭제 안함)
> 

`RMDIR` : 디렉토리(폴더)를 삭제

```cmd
C:\Users\kosmo\Documents>rmdir Sample
디렉터리가 비어 있지 않습니다.

C:\Users\kosmo\Documents>rmdir /s Sample
Sample, 계속하시겠습니까(Y/N)? y

C:\Users\kosmo\Documents>dir
 C 드라이브의 볼륨에는 이름이 없습니다.
 볼륨 일련 번호: EA47-CF2A

 C:\Users\kosmo\Documents 디렉터리

2021-05-14  오후 12:03    <DIR>          .
2021-05-14  오후 12:03    <DIR>          ..
2017-10-24  오후 07:13            26,257 Welcome to Cell.cell
2017-10-24  오후 07:20            23,552 Welcome to Hwp.hwp
2019-02-20  오후 05:38           219,962 Welcome to Show.show
2019-02-20  오후 05:31            15,185 Welcome to Word.hwdt
2021-05-12  오후 02:50    <DIR>          Zoom
               4개 파일             284,956 바이트
               3개 디렉터리  181,963,366,400 바이트 남음
```

`/s` 하위폴더까지 삭제

#

바탕화면에 폴더 생성

```cmd
C:\Users\kosmo>mkdir Desktop\Work
```

#

```cmd
C:\Users\kosmo>dir *.java
 C 드라이브의 볼륨에는 이름이 없습니다.
 볼륨 일련 번호: EA47-CF2A

 C:\Users\kosmo 디렉터리

2021-05-14  오전 10:51               167 HelloJava.java
2021-05-14  오전 11:07               138 MyName.java
               2개 파일                 305 바이트
               0개 디렉터리  181,961,322,496 바이트 남음

C:\Users\kosmo>dir /s *.java
```

자바 파일 찾기. `/s` 는 하위까지 찾음

#

`move` : 파일을 이동

```cmd
C:\Users\kosmo>move *.java Desktop\Work
C:\Users\kosmo\HelloJava.java
C:\Users\kosmo\MyName.java
        2개 파일을 이동했습니다.
```  
> java 항목들을 모두 이동

#

```cmd
C:\Users\kosmo>rmdir /s hello kosmo
hello, 계속하시겠습니까(Y/N)? y
kosmo, 계속하시겠습니까(Y/N)? y
```

> 하위 폴더까지 여러개 삭제. 휴지통에 가지 않음으로 주의 필요.
> 



----

## 재실습

파일 옮긴 뒤 재 실습.


```cmd

새로 컴파일

C:\Users\kosmo\Desktop\Work>javac -d . MyName.java  
C:\Users\kosmo\Desktop\Work>javac -d . HelloJava.java

새로 java 실행

C:\Users\kosmo\Desktop\Work>java -cp . hello.HelloJava
Hello, Java
안녕, java

C:\Users\kosmo\Desktop\Work>java -cp . kosmo.MyName
내 이름은 Kosmo 입니다
```  


## 실습 2

```  
메인클래스. 하나의 패키지에서 하나의 클래스.

패키지를 기준으로.

`public` 클래스는 두개이상 들어가면 안됨. `public`은 없어도 무방하긴 함.

패키지 하나에 하나의 클래스.

자바의 버전업에 따라서 달라짐.

버전업에 따라 문법체계가 달라짐.  
```

- 한꺼번에 컴파일 

- 과제

```
자바 패키지 실습2  

• 작업디렉토리: Desktop\Work\   
  – 작업디렉토리: Desktop\Work\mystudent\
  
• Main Class name: MyStudent   
– Package name: kosmo   
– 결과 출력:     
	• “kosmo 학생입니다”   

• Class name: Summary 
– Package name: kosmo

• MyStudent, Summary 컴파일하고 Main class를 실행하시오  
```

```java

메모장 소스코드 작성

메인클래스 MyStudent 작성한것.

package kosmo;

public class MyStudent {

	public static void main(String[] args) {
		System.out.println("kosmo 학생입니다");
	}
}

클래스 Summary 작성한것.

package kosmo;

public class Summary {
	// To do
}

```


```cmd
한꺼번에 컴파일 실행.

C:\Users\kosmo\Desktop\Work>javac -d . MyStudent.java Summary.java
```

> 컴파일이 정상적으로 됨.  

```cmd
C:\Users\kosmo\Desktop\Work>java -cp . kosmo.MyStudent
kosmo 학생입니다
```

> Main class도 정상적으로 실행 됨.

#

에드위드

위키독

OS, 

컴퓨터구조 등 따로 공부해보기

프로세스 관련. 공부 따로 해보기

#

----


## 오후수업  

- 프로그램실행은 메모리를 할당받는 행위  
- 메모리가 부족하면 대기열 발생  
- OS가 메모리 관리 (Process Management)   
- 모든 io 는 FileSystem에서 관리  
- [jvm 성능관련](https://www.holaxprogramming.com/2017/10/09/java-jvm-performance/)  




- 이클립스 다운  

에디터마다 다름.

Eclipse IDE for Java Developers  
에디터 + J

java SE : 일반사용자용  
java EE : 엔터프라이즈용 (보안관련 추가)  

#

이클립스 

> 이클립스 설치 후 둘러보기.  
> 

[이클립스 설치](https://www.eclipse.org/downloads/packages/)  

컨트롤+스페이스 --> JRE 보조.

package Expolor 창에서 -> 파일 오른쪽버튼 -> properties -> text file encoding  
기본은 윈도우용 MS949

워크스페이스를 유니코드로 미리 해놓으면 다른환경에서 이상이 없음. 

```- 설정방법
Window -> Preperences -> encoding 검색 -> 각탭 부분에서 text file encoding 부분항목들을 UTF-8로 각각 변경해준다.

```

ex) 리눅스 환경에서 그대로 사용할수 있음.


#

- 변수  : 저장할 공간의 이름.

```java
이클립스 실습 (변수 선언하여 사용하기) 책 45p

package chapter2;

public class Variable1 {

	public static void main(String[] args) {
		// type : primitive type, object type(class)
		
		int level;			//정수형 변수 level을 선언
		level = 10;			//level 변수에 값 10을 대입
		System.out.println(level);	//level 값 출력

	}

}
```

#

```java
package chapter2;

public class Variable1 {

	public static void main(String[] args) {
		// type : primitive type, object type(class)
		
		int level;			//정수형 변수 level을 선언
		level = 10;			//level 변수에 값 10을 대입
		System.out.println(level);	//level 값 출력

		System.out.println("Hello, Java"); //"Hello, Java" <---객체이다.
		
		//primitive type 을 다 제외하고 숫자이다.
		
//52p 참고
//		String str = "Hello, java";
//		String str = new String("Hello, java")
		//위의 System.out.println("Hello, Java"); 과 같은것 ( 61p 리터럴형 )
		
	}

}

```
#


level 값을 `//주석처리` 해서 나온 에러.

```java
Exception in thread "main" java.lang.Error: Unresolved compilation problem: 
	The local variable level may not have been initialized

	at chapter2.Variable1.main(Variable1.java:10)
```

> 메모리에 배정된 값이 없어서 생긴 `Exception Error` -> `not have been initialized` 이다.





#

추가사항

```java
package chapter2;

public class Variable1 {

	public static void main(String[] args) {
		// type : primitive type, object type(class)
		
		int level;			//정수형 변수 level을 선언
		level = 10;			//level 변수에 값 10을 대입
							//숫자 리터럴
		
		
		System.out.println(level);	//level 값 출력

		System.out.println("Hello, Java"); //"Hello, Java" <---객체이다.
		
		//primitive type 을 다 제외하고 숫자이다.
		
//52p 참고
//		String str = "Hello, java";    //문자 리터럴
//		String str = new String("Hello, java")  // new operator
		
		//위의 두가지랑 System.out.println("Hello, Java");은 같은것 ( 61p 리터럴형 )
		//원래는 new가 들어가야 하지만 ...  (45~46p)
		

		// 2. 변수이름 사용
		int q_level;
		int count100;
		int _master;
		int $won;
		
		int !won;
		
		int 27day;
		int 1abc;
		
		int package;
		int new;
		int class;
	
		
		
		
	}

}
```

> 변수이름 사용항목들 이클립스에서 보면 에러 사항을 볼 수 있다.
> 

#

추가설명  

```java
package chapter2;

public class Variable1 {

	public static void main(String[] args) {
		// type : primitive type, object type(class)
		
		int level;			//정수형 변수 level을 선언
		level = 10;			//level 변수에 값 10을 대입
							//숫자 리터럴
		
		
		System.out.println(level);	//level 값 출력

		System.out.println("Hello, Java"); //"Hello, Java" <---객체이다.
		
		//primitive type 을 다 제외하고 숫자이다.
		
//52p 참고
//		String str = "Hello, java";    //문자 리터럴
//		String str = new String("Hello, java")  // new operator
		
		//위의 두가지랑 System.out.println("Hello, Java");은 같은것 ( 61p 리터럴형 )
		//원래는 new가 들어가야 하지만 ...  (45~46p)
		

		/* 2. 변수이름 사용
		int q_level;
		int count100;
		int _master;
		int $won;
		
		int !won;
		
		int 27day;
		int 1abc;
		
		int package;
		int new;
		int class;
		*/ //주석처리를 해제하고 이클립스에서 보면 에러 이유를 확인 할 수 있다.
		
		
		// 의미있는 변수 선업!
		
		/*int ns;					// 학생수
		int numberOfStudent;	// 학생수
		
		int studentIsGraduated; // 졸업여부?
		*/
		
		//소문자로 시작 다음문장 시작 접속어 앞부분은 대문자. ->> 카멜 표기법.
		
	}

}
```

#

## 마지막교시 실습

```java
package hello;

public class SizeOfTypes {

	public static void main(String[] args) {
		// byte -> Byte
		System.out.println("byte 크기: " + (Byte.SIZE/8) + "Bytes"); // primitive type 마다 클래스 크기 정의가 있다.
		// Int -> Integer
		// Short -> Short
		// Long
		// Character
		// Float
		// Double

		System.out.println("Int 크기: " + (Integer.SIZE/8) + "Bytes");
		
		System.out.println("Short 크기: " + (Short.SIZE/8) + "Bytes");
		
		System.out.println("Long 크기: " + (Long.SIZE/8) + "Bytes");
		
		System.out.println("Char 크기: " + (Character.SIZE/8) + "Bytes");
		
		System.out.println("Float 크기: " + (Float.SIZE/8) + "Bytes");
		
		System.out.println("Double 크기: " + (Double.SIZE/8) + "Bytes");
	
		
		// 책 49p 실습.
	}

}
```



과제 (숙제) 

운영체계

1. 메모리  
2. 프로세스  

자료를 찾아 공부하고, 공부한 내용을

각 2장씩 요약 설명.

ppt, word 무방 , 깃허브 페이지링크도 무방

5/16 12:00까지

강사 이메일로 전송










































