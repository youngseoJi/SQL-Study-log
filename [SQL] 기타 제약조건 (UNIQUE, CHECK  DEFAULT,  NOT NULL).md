[핵심 제약조건 기본키 , 외래키 설명 및 데이터의 무결성 설명 ](https://velog.io/@estell/SQL-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%A0%9C%EC%95%BD%EC%A1%B0%EA%B1%B4)

---

# 고유키 : UNIQUE
- 고유키 제약조건 : "중복되지 않는 유일한 값" 이어야함. -> 기본키 id 유사하게 사용
- NULL 값 허용 -> 필수값 X
- 한 테이블에 고유키를 여러개 설정 가능
> 고유키와 기본키의 차이점
기본키와 비슷하지만, 기본키는 테이블에 1개 만 지정이 가능하고, null 값을 허용하지 않음

## 고유키 지정방법

> [컬렴명]데이터타입(길이) **UNUQUE**


```sql
create table member
( mem_id char(8) not null primary key,
  mem_name varchar(10) not null,
  height tinyint unsigned null,
  email char(30) null unique
  );
  
```

![](https://velog.velcdn.com/images/estell/post/7e6c83bf-166e-4928-afac-d74be25adbca/image.png)


- 오류발생
email 은 UNIQUE 고유키이므로 중복되는 이메일은 1번만 입력된다. 중복 X

>![](https://velog.velcdn.com/images/estell/post/cfd47e1f-da02-486a-96ef-7c339914c221/image.png)![](https://velog.velcdn.com/images/estell/post/523c2c03-05d2-4c3e-ab0f-34b7dae58e1a/image.png)

---

# CHECK 
- 체크의 제약조건: "입력되는 데이터를 점검" 함.
- 데이터의 무결성 -> 조건에 맞지않는 데이터를 거름



## 체크 지정방법
> [컬럼명][데이터타입](길이) **CHECK**


```sql
create table member
( mem_id char(8) not null primary key,
  mem_name varchar(10) not null,
  height tinyint unsigned null check(height >= 100),
  email char(30) null
  );
```
![](https://velog.velcdn.com/images/estell/post/4259a89a-b98e-475e-ab37-102c6a41ee3b/image.png)


- check 제약조건 예시)
check(height >= 100), 체크 제약조건의 100이상이 되지않는 키는 입력되지 않는다.

```sql 
insert into member values('EST', '에스텔', 166, 'egeg@gmail.com');
insert into member values('JYP', '박진영', 188, 'jyp@gmail.com');
insert into member values('SM', '이수만', 90, 'sm@gmail.com');
```  
![](https://velog.velcdn.com/images/estell/post/37555e48-3266-4fa9-8ba1-53cb49d7d53a/image.png)![](https://velog.velcdn.com/images/estell/post/64660b9c-5629-49fe-ae91-943d2503c8e0/image.png)

### 기존 테이블에 CHECK 제약조건 지정
ALTER 테이블변경문 사용, ADD CONSTRAINT 옵션으로 생성되어있는 기존 테이블에 제약조건을 지정한다.

- ADD CONSTRAINT명령은 테이블이 이미 생성된 후 제약 조건을 생성하는 데 사용

```sql
alter table member
add constraint
check (phone1 in ('02','031', '032'));

```

- check 제약조건 예시2)
check 제약조건을 걸어놓은, 지역번호가 아닌 핸드폰 번로 010을 입력하자 입력되지 않음. 

```sql
insert into member values('HL', '헬로', 162, '010');
insert into member values('HI', '하이', 162, '02');
``` 
![](https://velog.velcdn.com/images/estell/post/261ac2e4-dff6-48e7-a57a-0a19f89c283e/image.png)![](https://velog.velcdn.com/images/estell/post/c36848a0-047e-40a8-8ccc-4f92b4491185/image.png)



---

# 기본값 : DEFAULT 
- 기본값 제약조건 : 기본값 정의는 값을 입력하지 않았을경우 "자동으로 입력될 기본값을 미리 지정해 놓는 것"

## 기본값 정의방법

> [털럼명][타입](길이) **DEFAULT**


- height 컬럼 제약조건 지정 예시) DEFAULT 기본값 160으로 정의함 

```sql
create table member
( mem_id char(8) not null primary key,
  mem_name varchar(10) not null,
  height tinyint unsigned null default 160,
  phone1 char(3) null
  );
```
![](https://velog.velcdn.com/images/estell/post/6eb19690-f06b-43cd-a78a-530a8a6063f0/image.png)

### 기존 테이블에 DEFAULT 제약조건 지정
ALTER 테이블 및 컬럼 변경문 사용함.
> **SET DEFAULT '자동입력될 기본값'**

```sql
alter table member
alter column phone1 set default '02';
```
![](https://velog.velcdn.com/images/estell/post/7e608fe0-8b83-4b9f-8916-0bbe6357845d/image.png)


- DEFAULT 로 지정한 값을 사용한다.

```sql
insert into member values('RED', '레드벨벳', 158, '02');
insert into member values('SM', '이수만', default, default);
```
![](https://velog.velcdn.com/images/estell/post/21a77e6a-0b91-42a6-93d8-7c84ed833200/image.png)

---
# NOT NULL / NULL 
-  NULL : NULL 값 혀용
   - 해당 컬럼이 필수 값이 아닌 경우 사용 
- NOT NULL : NULL 값 허용 X
   - 해당 컬럼이 필수 값인 경우 사용 

기본적으로 NULL/NoT NULL 제약조건 생략시 **NULL** 로 인식한다. 
>BUT **기본키 PRIMARY KEY / 기본깂 DEFAULT** 제약조건에서의 생략은 **NOT NULL**로 인식한다.


