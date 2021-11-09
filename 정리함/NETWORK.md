# 네트워크 2021/11/09  
## 네트워크
두 대 이상의 컴퓨터들을 연결하고 통신할 수 있는 것   
## 통신망  
전자 신호를 통해 통신하는 모든 기기가 서로 통신하기 위한 하나 이상의 망을 의미 ex) LAN, WAN, MAN  
## 인터넷 
 TCP/IP라는 통신 프로토콜을 이용한 컴퓨터 네트워크  
## TCP/IP
>컴퓨터 사이의 통신 표준 및 네트워크의 라우팅 및 상호연결에 대한 자세한 규칙을지정하는 프로토콜 스위트, 인터넷에서 광범위하게 사용.
>네트워크를 연결하는 자세한 규칙
>>**TCP (Transmission Controll Protocol)**  
>>*통신 제어 
>>두 컴퓨터 간의 전송 계층*  
>>**IP (Internet Protocol Address)**    
>>*통신 장치들이 서로를 인식하고 통신을 하기 위해 사용하는 특수한 번호*   
>>ex  
>>집주소 (집 1개 -> 1개 주소) : 컴퓨터 주소 (컴퓨터 1개 -> 1개 IP)  
>>택배 (쿠팡 -> 집 )         : 통신 (PC방 -> 학원)  
>>네이버접속 (학원 ip ---> 네이버 ip 서버실)
>>ip : 숫자 0~255, 4자리, 구분
>>ip는 사람이 사이트마다 외우기 힘들기 때문에 문자로 변환
>>ip ---> 문자 : 도메인 주소(DNS)  
## 현재 IP확인법
>CMD -> ipconfig  
>![image](https://user-images.githubusercontent.com/88884623/140850321-49d43a06-5de4-4c7d-a401-6ca0c7e976f0.png)  
>JAVA -> InetAddress 클래스 사용  
## 호스트 가져오기
**InetAddress 클래스 사용**  
```java
package A;

import java.net.InetAddress;

public class NetworkStudy {

public static void main(String[] args) {

		//1. 현재 pc의 호스트 가져오기
		try {
			InetAddress inetAddress = InetAddress.getLocalHost();//무조건 예외처리
			System.out.println("현재 pc의 정보객체 : " + inetAddress);
			System.out.println("현재 pc의 이름 : " + inetAddress.getHostName());
			System.out.println("현재 pc의 주소 : " + inetAddress.getHostAddress());
      
		//2. 네이버 회사의 호스트 가져오기
			InetAddress inetAddress2 = InetAddress.getByName("www.naver.com");
			System.out.println("네이버 회사의 정보객체 : " + inetAddress2);
			System.out.println("네이버 회사의 이름 : " + inetAddress2.getHostName());
			System.out.println("네이버 회사의 주소 : " + inetAddress2.getHostAddress());
			
		//3. 네이버 회사의 다수 IP 확인
			InetAddress[] inetAddresses = InetAddress.getAllByName("www.naver.com");
			for(InetAddress address : inetAddresses) {
				System.out.println("네이버 배열 내 PC 이름 : " + address.getHostName());
				System.out.println("네이버 배열 내 PC 주소 : " + address.getHostAddress());
			}
		//4. 페이스북 회사의 IP 확인	
			InetAddress inetAddress3 = InetAddress.getByName("www.facebook.com");
			System.out.println("페이스북 pc의 정보객체 : " + inetAddress3);	
		} catch (Exception e) {
			// TODO: handle exception
		}
	}
```  

## 실행 결과 
![image](https://user-images.githubusercontent.com/88884623/140851737-adc6d089-eb47-4bde-876d-260d88af5a14.png)


## 통신용 서버 만들기
>ServerSocket 클래스 사용  
>소켓 : 네트워크 상에서 동작하는 프로그램들(PC) 간의 통신의 종착점  
>	클라이언트 소켓에서 연결 요청(올바른 연결일 경우)을 하면 서버 소켓이 허락해서 통신할 수 있도록 연결  
>
```java
```
