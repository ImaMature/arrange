# 인터페이스
## 인터페이스 ATM 
```java
package Interface;

public interface ATM {
	//필드는 무조건 상수
	//상수 : 절대바뀌지 않는 값 (public static final을 안써도 자바 컴파일러에서 자동으로 컴파일 해준다.)
	//추상메소드 : 선언 O,  정의X, 인수 있을수도 있음
	//실행할 클래스가 필요. 그 클래스는 은행.java
	
	public void 계좌등록();
	public void 계좌이체();
	public void 예금();
	public ATM 출금(); //public void 메소드(); == public 인터페이스명 메소드();
	public ATM 계좌잔고(); //public (abstract) void or 인터페이스명 메소드(); => 기본적으로 abstract를 선언하지 않아도 자바 컴파일러가 자동으로 컴파일해줌. 
	
	//추상클래스말고 인터페이스를 쓰는 이유?
	//추상클래스는 1번밖에 상속이 안되지만, 인터페이스는 다중 상속이 가능하기 때문
	
	default void 디폴트() {
		System.out.println("디폴트메소드실행");
	}
}
```
## 인터페이스를 구현할 클래스
```java
package Interface;

public class 은행 implements ATM{
	//인터페이스를 실행할 클래스 (구현(implements) 클래스)
	//인터페이스에 있는 추상메소드들을 실행.

	//필드
	String 계좌번호;
	int 예금액;
	@Override
	public void 계좌등록() {
		System.out.println("계좌등록");
	}
	@Override
	public void 계좌이체() {
		System.out.println("계좌이체");
		
	}
	@Override
	public void 예금() {
		System.out.println("예금");
		
	}
	@Override
	public ATM 출금() {
		System.out.println("출금");
		return null;
	}
	@Override
	public ATM 계좌잔고() {
		System.out.println("잔고");
		return null;
	}

```
## 상속받은 클래스1
```java
package Interface;

public class 국민은행 extends 은행{
	//은행(구현) 클래스를 상속, ATM에 있는 메소드도 사용가능.

	
  
	@Override
	public void 계좌등록() {
		System.out.println("국민은행 계좌등록");
		
		
	}
}
```
## 상속받은 클래스2
```java
package Day09;

public class 신한은행 extends Bank{
	
	final String 은행코드 = "01"; //상수
	
	@Override
	public void 계좌등록 () {
	 System.out.println("신한은행 계좌등록");
 }
}
```
## 메인 메소드가 있는 클래스
```java
package Interface;

public class BankMain {
//메인 메소드 클래스

	//1. 계좌 프로그램 [ 상속, 인터페이스 ]
		// ATM [인터페이스]
			// 추상메소드 : 계좌등록, 예금, 출금, 이체, 잔고
		//1. 은행 [슈퍼클래스]
			// 필드(속성) : 계좌번호, 예금액
			// 메소드(행동) : 계좌등록, 예금, 출금, 이체, 잔고
		//2. 국민은행 [서브클래스]
	
		//3. 신한은행 [서브클래스]
	public static 은행 [] arr = new 은행 [100];
	public static void main(String[] args) {
		ATM a = new 국민은행();
		a.계좌등록();
		a.계좌이체();
		a.계좌잔고();
		a.디폴트(); //국민은행 클래스에서 오버라이딩을 따로 하지 않았기 때문에 인터페이스에 있는 메소드 그대로 출력됨
		
		System.out.println();
		
		ATM b = new 신한은행();
		b.계좌등록();
		b.계좌이체();
		b.계좌잔고();
		b.디폴트(); 
		b.예금();
		b.출금();
		
		//5. 슈퍼클래스와 서브클래스의 객체를 담을 수 있는 배열
		// 슈퍼클래스로 배열 선언
		은행 temp = new 은행();
		arr[0] = temp;
		국민은행 temp2 = new 국민은행();
		arr[1] = temp2;
		신한은행 temp3 = new 신한은행();
		arr[2] = temp3;
		
		arr[0] = new 은행();
		arr[1] = new 국민은행();
		arr[2] = new 신한은행();
	
	}
}
```

# 출력 값 <br>
![image](https://user-images.githubusercontent.com/88884623/140734578-55de2468-e815-4360-897d-4dde1beb4535.png)  
<br>
오버라이딩하지 않은 인터페이스의 메소드는 그대로 출력된다.
반면 오버라이딩한 메소드들은 바뀌어서 출력된다.


