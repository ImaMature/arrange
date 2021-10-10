
# 2021.10.10
>**README.md 작성법**<br>
>README.md 파일의 작성은 MARKDOWN을 사용합니다. *확장자 md가 바로 이 MARKDOWN의 확장자명입니다.*
---
# MARKDOWN
MARKDOWN 정리, 실습 for README.md

# 1. 제목(글머리) 작성
# H1 제목  
## H2 부제목
### H3 소제목
#### H4 제목4
##### H5 제목5
###### H6 제목6


# 2. 번호 없는 리스트 작성
* 리스트1
  - 리스트2
    + 리스트3
    
# 3. 번호 있는 리스트 작성
1. 리스트1
2. 리스트2
3. 리스트3 

# 4. 이텔릭체(기울어진 글씨) 작성
*텍스트*

# 5. 굵은 글씨 작성
**텍스트**  
***텍스트*** (볼드 + 이텔릭)
# 6. 인용
> 인용1

> 인용2
>> 인용안의 인용

# 7. 수평선 넣기

---
  
# 8. 링크 달기
(1) 인라인 링크  

[구글 주소](https://www.google.com)

(2) 참조 링크  

[블로그 주소][blog]

[blog]: https://lsh424.tistory.com/

# 9. 이미지 추가하기
**1) 깃허브 레포지토리에서 이슈 클릭**<br>
![image](https://user-images.githubusercontent.com/88884623/136684899-e297a290-1517-4f9a-bc58-1a5c8bb41d25.png)
<br><br>**2) New Issue 클릭**
![image](https://user-images.githubusercontent.com/88884623/136684922-5a9e2637-017b-4783-bceb-f43a2e339ec8.png)
<br><br>**3) 이미지 드래그 & 드랍**
![드래그앤드랍](https://user-images.githubusercontent.com/88884623/136685051-52ccaadc-878b-483e-9221-14b413fe9bc2.png)
<br><br>**4) 생성된 텍스트를 README.me에 복사&붙여넣기**
![image](https://user-images.githubusercontent.com/88884623/136685101-bdd0f50a-4c4a-4293-9b24-53a3fe68de31.png)
![ad](https://user-images.githubusercontent.com/88884623/136685420-4e93d35b-7778-42d9-bca6-5e2c8af0735a.png)
<br><br>
**결과물**
<br>![navideul(butterflies)](https://user-images.githubusercontent.com/88884623/136684788-7846f309-6fc1-4c9b-8d7a-98b155cf100f.jpg)<br>

### 이미지 사이즈 조절
<img src="https://user-images.githubusercontent.com/31477658/85016059-f962aa80-b1a3-11ea-8c91-dacba2666b78.jpeg"  width="700" height="370">

### 이미지 파일로 추가하기
<img src="Capri_Island.jpeg" width="700"><br>
\*프로젝트 폴더 안에 넣어서 추가할 때 사용.

# 10. 코드블럭 추가하기

```swift
public struct CGSize {
  public var width: CGFloat
  public var heigth: CGFloat
  ...
}
```

# etc

**텍스트 굵게**  
~~텍스트 취소선~~

### [개행]  
**방법 1. 문장 마지막에 스페이스 두 번 이상 입력**
스페이스바를 통한 문장개행  
스페이스바를 통한 문장개행<br>  
**방법 2. html "\<br>" 태그 이용**  
br태그를 사용한 문장개행
<br>
<br>
br태그를 사용한 문장개행<br>
****엔터 하나를 입력하면 줄바꿈이 되지 않음***

### [체크박스]

다음과 같이 체크박스를 표현 할 수 있습니다. 
* [x] 체크박스
* [ ] 빈 체크박스
* [ ] 빈 체크박스

### [이모지 넣기]
window key + . (윈도우 로고 키 + 마침표)
❤️💜💙🤍🤣😂😊✌🤞😉👍

### [표 넣기]
|왼쪽 정렬|가운데 정렬|오른쪽 정렬| 
|:---|:---:|---:| 
|내용1|내용2|내용3| 
|내용1|내용2|내용3| 

<br>

### 정리내용(출처)
[sh9404님의 블로그]
(https://lsh424.tistory.com/37)
