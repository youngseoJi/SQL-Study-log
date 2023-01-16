# ALTER TABLE

생성해놓은 테이블의 열(컬럼)과 각 열마다의 제약조건을 추가, 삭제, 수정하는데에 사용된다.
(테이블 열(컬럼), 행 수정 X)

- user 공통 테이블 구성, 제약조건
- 구조 확인방법 desc user;

![](https://velog.velcdn.com/images/estell/post/573513df-fd3c-438e-9e77-6169eb889f56/image.png)


---

## 열추가 :  ADD 

>**ALTER TABLE** [테이블명]  
**ADD** [추가할 컬럼명][데이터타입(길이)];

-  예시) user 테이블에 데이터타입이 varchar(30)인 adress 컬럼 추가
> alter table user
add adress varchar(30);
![](https://velog.velcdn.com/images/estell/post/3d7e3ff5-ee0a-4abf-889a-38a5c40be096/image.png)





## 컬럼 삭제 : DROP 
>**ALTER TABLE** [테이블명]  
**DROP ** [삭제할 컬럼명];

-  예시) 
> alter table user 
drop adress;
> ![](https://velog.velcdn.com/images/estell/post/c23373d5-b4cf-419b-995b-2b4b4f381c7f/image.png)



## 컬럼 수정 - 데이터 유형변경 : MODIFY
>**ALTER TABLE** [테이블명]  
**MODIFY** [컬럼명][수정 데이터타입(수정 길이)];

-
>  alter table user  
modify user_email char(30);
![](https://velog.velcdn.com/images/estell/post/4a8bbac7-5212-44ff-a699-5eabe86627ea/image.png)


## 컬럼명 변경 : RENAME TO

데이터 타입 변경 (MODIFY)
>**ALTER TABLE** [테이블명]  
**RENAME** [기존 컬럼명] TO [수정 컬럼명];

-  예시) 
> 유저 테이블의 age 컬럼명을 use_age로 변경
alter table user 
rename age to user_age;
![](https://velog.velcdn.com/images/estell/post/38f9a560-7b3d-4773-9ede-c584fff90d17/image.png)





## 컬럼명과 데이터타입 동시변경 : CHANGE
>**ALTER TABLE** [테이블명]  
**CHANGE** [기본 컬럼명][수정 컬럼명][데이터타입(길이)];

-  예시) 
> alter table user  
change user_email user_이메일 varchar(25);
![](https://velog.velcdn.com/images/estell/post/d12d3b26-6bc6-46db-a57b-02373375d7b6/image.png)




> https://www.w3schools.com/sql/sql_alter.asp
