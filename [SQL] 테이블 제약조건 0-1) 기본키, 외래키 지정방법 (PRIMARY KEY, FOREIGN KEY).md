## 테이블 제약조건

제약조건은 데이터의 무결성을 지키기 위해 제한하는 조건으로, 테이블에는 기본키, 외래키 같은 제약조건을 설정할 수 있다.

> 데이터의 무결성이란? 데이터의 결함이 없다는 것이다.   
아이디가 중복될경우 메일 등 혼란이 온다(데이터 결함),  이런 결함이 없는 것이 데이터의 무결성이다.   
> => 해결하기 위해 기본키 PRIMARY KEY  제약조건이 있는 것! 

|제약|설명|
|---|---|
| AUTO_INCREMENT | 새 행 생성(행 데이터가 추가될 때 마다) 자동으로 1씩 증가 +  PRIMARY KEY|
| PRIMARY KEY | 중복 입력 불가, NULL(빈 값) 입력 불가(무조건 값이 있어야함)|
|FOREIGN KEY | 필수 X, 참조|
| UNIQUE | 중복 입력 불가|
| NOT NULL | NULL(빈 값) 입력 불가(무조건 값이 있어야함)|
| UNSIGNED | (숫자일시) 양수만 가능|
| DEFAULT 정의| 값 입력이 없을 시 기본값|

## PRIMARY KEY (기본키) 
- 각 테이블에는 1개만 지정 가능 => 테이블을 나타내는 id 같은 것
- 데이터를 구분할 수 있는 식별자로 사용된다.
- 무조건 NOT NULL, NULL 값 허용 X => 식별자는 필요하다
- 연결되는 두 테이블 중 기준테이블(기준이 되는)에 위치한다.
 > ex) 기준테이블인 회원테이블에 존재하는 아이디는 참조테이블인 구매테이블의 구매한 사람 아이디(외래키) 데이터가 없을 수 있다.
- 기본 키로 생성한 것은 자동으로 클러스터형 인덱스가 생성된다.
(예를들어, 책의 색인처럼 각 번호로 데이터를 빠르게 찾을 수 있다.)
- 보편적으로 AUTO_INCREMENT와 함께 사용한다. 


## 기본키 지정 방식
### 테이블 생성과 동시에, 기본키 지정

- 기본키를 지정하는 컬럼의 제약조건들 설정과 함께 기본키 지정
```sql
create table member 
( mem_id char(8) not null primary key,
  mem_name varchar(10) not null,
  height tinyint unsigned null
);
```

- 기본키를 지정하려는 컬럼의 제약조건 생성후, 
  해당 테이블의 맨 밑에 해당 컬럼이 기본키임을 지정
```sql

create table member 
( mem_id char(8) not null,
  mem_name varchar(10) not null,
  height tinyint unsigned null,
  PRIMARY KEY (mem_id)
);
```
- 동일한 결과
![](https://velog.velcdn.com/images/estell/post/0105a1ce-37cc-4ae7-83e7-96ae248de4b6/image.png)


### 기본키가 없는 기존 테이블에 기본키 지정
테이블을 변경하는 alter table 문을 사용하며, ADD CONSTRAINT 옵션을 통해 기본키를 생성한 테이블에 이후 지정해줄 수 있다.  

>**ALTER TABLE 테이블 ADD CONSTRAINT**



---


## FOREIGN KEY(외래키)
- 각 테이블에 여러개가 지정 가능하다. 
- 외래키는 두 테이블 사이의 관계를 연결해준다. => 참조하기 위한 키!
- 연결되는 두 테이블 중 참조테이불에 위치한다.
>  이때 외래키는 데이터의 무결성을 지켜주는 역할을 한다. 
ex) 참조테이블의 구매테이블의 구매한 사람의 아이디는 모두 다 => 기준테이블인 회원 테이블의 아이디에 있다


## 외래키 지정하는 방법

> **FOREIGN KEY(기준 테이블과 연결된 참조테이블 컬럼명) REFERENCES 테이블명 (기준테이블 기본키 컬럼명)**

-  참조 테이블 mem_id 컬럼을 외래키로 지정 -> 기준테이블 기본키 지정된 mem_id 컬럼과 연결
>```sql
create table buy
(  num int auto_increment not null primary key,
   mem_id char(8) not null,
   prod_name char(6) not null,
   foreign key(mem_id) references member (mem_id)
);
>```
![](https://velog.velcdn.com/images/estell/post/d6710f20-e0bc-4867-aee7-de499b39d7a0/image.png)

- 위의 참조테이블과 mem_id로 연결된 기준 테이블 (mem_id 컬럼 기본키 지정 상태) 
```sql
create table member 
( mem_id char(8) not null primary key,
  mem_name varchar(10) not null,
  height tinyint unsigned null
);

```

### 기본키 / 외래키가 없는 기존 테이블에 기본키 지정
테이블을 변경하는 alter table 문을 사용하며, ADD CONSTRAINT 옵션을 통해 기본키를 생성한 테이블에 이후 지정해줄 수 있다.  

>**ALTER TABLE 테이블 ADD CONSTRAINT**


### 기본키가 없는 테이블에 기본키 지정
>```sql
alter table member   
add constraint 
primary key  (mem_id);
>```
![](https://velog.velcdn.com/images/estell/post/fabd065d-0ac6-4764-b249-c9205e981805/image.png)
- 위에 해당하는 기본키가 없는 테이블
```sql
create table member 
( mem_id  CHAR(8) NOT NULL, 
  mem_name    VARCHAR(10) NOT NULL, 
  height      TINYINT UNSIGNED NULL
);
```
![](https://velog.velcdn.com/images/estell/post/d788a452-094d-4283-9e76-043607afee0e/image.png)

### 외래키가 없는 테이블에 외래키 지정

>```sql
alter table buy   
add constraint 
foreign key(mem_id) references member (mem_id);
```
![](https://velog.velcdn.com/images/estell/post/449d2b37-3e7d-4f00-bd21-4aa860770aad/image.png)


- 위에 해당하는 외래키가 없는 테이블

```sql
create table buy
(  num int auto_increment not null primary key,
   mem_id char(8) not null,
   prod_name char(6) not null
);
```
![](https://velog.velcdn.com/images/estell/post/a39e1ea7-c511-423f-8a03-50ff85395016/image.png)


-> 데이터 무결성 떄문에 수정, 삭제가 마음대로 되


---
>https://www.youtube.com/watch?v=BUHj-behLyc
