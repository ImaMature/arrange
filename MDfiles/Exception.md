20211109
# 예외처리 

## 예외 떠넘기기
>메소드 내부에서 예외가 발생할 것 같으면 기본적으로 *try-catch*문을 사용하지만 경우에 따라서는 메소드를
>호출한 곳으로 예외를 떠넘길 수도 있다. 이때 사용하는 키워드가 *throws*이다.
>*throws*는 메소드 선언부 끝에 작성되어 메소드에서 처리하지 않은 예외를 호출한 곳으로
>떠넘기는 역할을 한다. *throws* 키워드 뒤에는 떠넘길 예외 클래스를 쉼표로 구분해서 나열해준다.
>```java
>리턴타입 메소드명(매개변수,~) throws 예외클래스1, 예외 클래스2, ~ { }
>```
>다음처럼 *throws* *Exception*만으로 모든 예외를 간단히 떠넘길 수 있다.
>``` java
>리턴타입 메소드명(매개변수,~) throws Exception{ }
>```
>*throws*가 붙어있는 메소드는 반드시 *try*블록 내에서 호출되어야하며, *catch*블록에서 떠넘겨 받은
>예외를 처리해야 한다.

## 예외 발생시키기
**throw**
>1. 예외를 최초로 발생시키는 코드이다.
>2. throw로 발생된 예외는 일반적으로 생성자나 메소드 선언부에 throws로 떠넘겨진다.
>3. throw키워드 뒤에는 예외 객체 생성 코드가 온다.  
>
>``` java
>throw new XXXException();
>throw new XXXException("메시지");
>```
>대부분 자신을 호출한 곳에서 예외를 처리하도록 *throw*키워드로 **예외를 떠넘긴다**  
>``` java
>public static void method() thorws XXXException{
>   throw new XXXException("메시지");
> }
>```
>그렇기 때문에 *throws*키워드를 포함하고 있는 메소드는 다음과 같이 예외 처리를 해주어야 한다.
>```java
>try{
>   method();
>} catch(XXXException e) {
>   //예외처리  
>} 
>```

## 예외
**1. 사용자의 잘못된 조작, 개발자의 잘못된 코딩으로 인한 프로그램 오류**  

**2. 일반 예외 (Exception)**  
>자바 소스를 컴파일 하는 과정에서 예외 처리 코드가 필요한지 검사하므로 컴파일러 체크라고도 한다.
>*Exception*을 상속받지만 *Runtime Exception*을 상속받지 않는다.  

**3. 실행 예외 (Runtime Exception)**  
>컴파일하는 과정에서 예외 처리 코드를 검사하지 않는 예외
>개발자의 경험에 의해서 예외 처리 코드를 삽입해야 한다.
>*Runtime Exception*을 상속받는 클래스들이다.

## 멀티 catch
> *catch* 괄호 안에 동일하게 처리하고 싶은 예외를 |(shift+\) 로 연결하면 된다.
>> ``` java
>> catch(ArrayIndexOutOfBoundsException | NumberFormatException e){
>> } // 예외처리1
>> catch(Exception e){
>> } // 예외처리2
>> ``` 
>``` java
>catch (Exception e) {} catch(ClassNotFoundException e){}
>```
>	앞에 catch (Exception e)에있는 Exception이 예외들의 상위클래스라서 뒤에 것은 효력이 없다.

## ArrayIndexOutOfBoundsException
>배열에서 인덱스 범위를 초과하여 사용할 경우 발생
>```java
>public static void main(String[] args) {
>   String data1 = args[0];
>   String data2 = args[1];
>
>   System.out.println("args[0] : " + data1);
>   System.out.println("args[1] : " + data2);
>}
>//3라인에서 두 개의 실행 매개 값을 주지않았기 때문에 오류 발생
>```

## NullPointerException
>가장 빈번하게 발생하며 객체 참조가 없는 상태인 null값을 갖는 참조 변수로 객체 접근 연산자인 도트(.)를 사용했을 때 발생

## NumberFormatException
> 숫자로 변환될 수 없는 문자가 포함되어 있을 경우 발생

## ClassCastException
> 타입 변환(캐스팅)은 상위 클래스와 하위 클래스 간에 발생하고, 구현 클래스와 인터페이스 간에도 발생한다.
> 이러한 관계가 아니라면 클래스는 다른 클래스로 타입 변환할 수 없는데 강제로 하려고 할 때 이 예외가 발생한다.
> ``` java
> Animal animal = new Dog();
> Cat cat = (Cat) animal;
> // 대입된 객체가 아닌 다른 클래스 타입으로 타입 변환했기 때문에 에러 발생
> ```

## instanceof
> 다른 클래스로 타입변환 가능한 지 확인하는 명령어
> ``` java
> Animal animal = new Dog();
> if(animal instanceof Dog) {
>   Dog dog = (Dog) animal;
> } else if (animal instanceof Cat) {
>   Cat cat = (Cat) animal;
> }  
> ```

## finally
> 예외와 상관없이 무조건 실행되는 블록으로 항상 실행된다.

## 예제  
```java
public static void main(String[] args) {
				String[] strArray = {"10","2a"};
				int value = 0;
				for (int i=0; i<=2; i++) {
					try {
						value = Integer.parseInt(strArray[i]);		
					}												
					catch (ArrayIndexOutOfBoundsException e) {
						System.out.println("인덱스를 초과했음");
					}
					catch (NumberFormatException e) {
						System.out.println("숫자로 변환할 수 없음");
					} 
					finally {
						System.out.println(value);
					}
				}
			}
 ```    
출력결과는?   
>i == 0 => strArray[0] => 예외 발생 X => 예외가 없기 때문에 finally로 이동 => 10 출력
>  
>i == 1 => strArray[1] => 예외 발생 O(a10=문자열이기 때문) => finally로 이동 =>  
>(초기화한 값인 int value = 0으로 배열의 0번째 인덱스 값 출력) value = 10출력, 예외도 발생  
>발생한 예외는 catch문으로 이동 => NumberFormatException e로 이동 => 숫자로변환할 수 없음 출력  
> 
>i == 2 => strArray[2] => 인덱스 없음 => 예외발생 => finally 출력 10  
>(초기화한 값인 int value = 0으로 배열의 0번째 인덱스 값 출력)value = 10 출력
>

 
