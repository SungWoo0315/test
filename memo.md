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

커맨드라인

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




























