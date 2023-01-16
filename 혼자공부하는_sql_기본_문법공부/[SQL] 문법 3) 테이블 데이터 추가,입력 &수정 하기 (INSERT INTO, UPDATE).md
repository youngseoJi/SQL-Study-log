>sql 복습 겸/ 과거 정리 글 보강하여 재업로드 중

---


## 테이블 행 데이터 추가하기
데이터베이스내의 테이블에 새로운 데이터를 추가(입력)한다.
>**INSERT INTO** 테이블명 (필드이름1, 필드이름2, ........) **VALUES ** ('문자열',123,....); 

###  테이블 행 데이터 한 줄씩 입력하기
>**INSERT INTO** user
(user_name, user_email, age)
**VALUES**
('영서','sql@gmail.com',30);
![](https://images.velog.io/images/estell/post/658a18cd-7210-436d-9e83-6516ac9fb0c0/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-03-07%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2010.38.28.png)

---

###  테이블 행 데이터 한번에 입력하기
- id는 테이블 구조를 만들 때 auto_uncrement로 설정해줘서 데이터가 증가함에따라 자동으로 1씩증가한 아이디를 붙여준다! 따로 id값은 입력해줄 필요없다.

>**INSERT INTO **user
(user_name, user_email, age)
**VALUES**
('명휘', 'mh@gmail.com', 40),
('봉봉', 'bb@gmail.com', 10),
('베리', 'vv@naver.vom', 6);

![](https://images.velog.io/images/estell/post/2a270618-5b2b-4adf-b3b2-9afc1e9a3a87/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-03-07%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2010.46.18.png)

---

## 테이블 행 데이터(레코드) 수정하기
>**UPDATA** 테이블명 SET 바꿀 열=데이터(레코드) WHERE 바뀔 열 = 데이터(레코드);

- UPDATE user 
SET user_name='명히' 
WHERE id=1;
=> user 테이블의 id가 1인 user_name 값을 '명히'로 변경해주세요
명위에서 명히로 변경된 것을 볼 수 있다.
![](https://images.velog.io/images/estell/post/dd88f88a-b458-4fec-9dc8-75ee87572291/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-03-07%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2011.27.28.png)

