# 메소드 호출하는 법 (중요!!!!!!!!!)

## 1.Controller 인스턴스 
* [다른 컨트롤러에서 동일한 Boardpane 사용] 계속 동일한걸 사용하기 때문에  new로 새롭게 객체생성하면 안됨
``` java
    public static MainpageController instance;	//변수 선언
	
    //생성자
    public MainpageController() {
    	instance = this; // [ this : 현재 클래스의 메모리(모든 필드, 메소드)를 instance변수에 할당 ]  동일한 Boardpane사용하기 위해서 this사용
		//this는 메소드영역
    }
    
    //객체 변환
    public static MainpageController getinstance() {
    	return instance;	instance 변수 호출 메소드
    }
   MainpageContoller.getinstance().loadpage("productegister") // 메소드 실행하기
```
## 2. Dao 인스턴스[해당 인스턴스 생성시 DB와 연결된 인스턴스 사용할 수 있음   
``` java
public static ProductDao productDao = new ProductDao(); //생성자 // new라서 스택영역으로 이동

	public ProductDao(){ //메소드 //커넥션을 계속해야되기때문에 메모리할당이 소모가 많이 돼서 클래스에 커넥션 생성자를 만들어놓은것
			try {
			Class.forName("com.mysql.cj.jdbc.Driver");
			connection = DriverManager.getConnection("jdbc:mysql://localhost:3307/javafx?serverTimezone=UTC", "root", "1234");
		} catch (Exception e) {}
	}//커넥션한걸 연결해주는거

public static ProductDao getProductDao() {return productDao;} //커넥션된거 호출

boolean result = ProductDao.getinstance().register(product);

ProductDao dao =new ProductDao(); //새로운 생성자를 통해 새로운 메모리영역에 저장
dao.update(product2); //저장된 걸 빼오기   
```
## 3. new 객체를 통한 메소드 접근   
``` java
클래스명 변수명 = new 클래스명()
변수명.메소드명()
```
## 4. static 메소드   
	>클래스명.메소드명()

* 코딩을 짤때 MVC를 생각하고 해야됨 입력받았을때, 객체화하기<br>
* 뭐해야될지 모르면 문법 생략하고 그림을 그려라<br>
* 어떤 걸 view에서 꺼내와야하는지 생각<br>
* 꺼내온걸 객체화 해서 dao를 통해 db에 넣어야겠다는 큰 흐름<br> 

### V : 입력받은것
```java
String p_name = txtpname.getText();
String p_contents = txtpcontents.getText();
int pprice = Integer.parseInt(txtpprice.getText());
String category = "";

    	if(opt_1.isSelected()) {category="의류";}
    	if(opt_2.isSelected()) {category="신발";}
    	if(opt_3.isSelected()) {category="가방";}
    	if(opt_4.isSelected()) {category="ACC";}
```   	
### C : 컨트롤에서 입력받은것 객체화 (객체화(캡슐화) 안시키면 6개 따로 넣어놔야됨)
```java
Product product2 = new Product(product.getP_no(), p_name, pimage, p_contents, category, pprice, 0, "0", 0); //자료형이 int형인지 아닌지
```
### M : 클래스(객체)<br>
* 꺼내올때 객체화<br>
```java
public boolean update (Product product) {
		<String sql = "update product set p_name=?, p_img=?, p_contents=?, p_category=?, p_price=? where p_no=?";
		
		try {
			preparedStatement = connection.prepareStatement(sql);
			preparedStatement.setString(1, product.getP_name());
			preparedStatement.setString(2, product.getP_img());
			preparedStatement.setString(3, product.getP_contents());
			preparedStatement.setString(4, product.getP_category());
			preparedStatement.setInt(5, product.getP_price());  //int형인지 아닌지
			preparedStatement.setInt(6, product.getP_no());
			preparedStatement.executeUpdate(); //query 는 select때만,
			return true;
		}catch (Exception e) {
			return false; // Observerlist만 {}밖에 나오는 return false를 씁니다. 
		}> 객체화
	}
```
### DB처리
```java
boolean result = ProductDao.getProductDao().update(product2)
```

### 이미지경로
윈도 창 하나가 stage인데, 이미지 경로 불러오기 할때 stage가 무조건 있다는 전제하에 사용<br>
* uri : \, 공백을 바이트로 표현<br>
* url : /<br>
```java
Image image = new Image( pimage ); 이미지 클래스에 경로 설정
pimg.setImage(image); 씬빌더로 만든 이미지뷰를 저장된 경로의 이미지로 전환
```
