

## 특정 컬럼 뒤에 컬럼 추가 : ADD AFTER



>**ALTER TABLE** [테이블명]  
**ADD** [추가할 컬럼명][데이터타입(길이)] **AFTER** [기준 컬럼명];

- 예시 : user_email 컬럼 뒤에 phone_num 컬럼을 추가한다.
> alter table user  
add phone_num varchar(12) after user_email;
![](https://velog.velcdn.com/images/estell/post/875c8000-1838-41ae-90b1-081444ff484b/image.png)

---

## 맨 앞에 컬럼추가 : ADD FIRST
- 기본적으로 맨뒤에 추가된다. 맨앞에 추가하는 방법

>**ALTER TABLE** [테이블명]  
**ADD** [추가할 컬럼명][데이터타입(길이)] **FIRST** ;

- 예시 : 테이블 맨 첫번째, 맨 앞에 height 컬럼을 추가한다.
> alter table user  
add phone_num varchar(12) after user_email;
![](https://velog.velcdn.com/images/estell/post/6bddbc18-9a81-4016-95cd-2367804aa1ec/image.png)


---

## 컬럼 위치 수정 : MODIFY AFTER


>**ALTER TABLE** [테이블명]  
**MODIFY** [이동할 컬럼명][데이터타입(길이)] **AFTER** [기준 컬럼명];

- 예시 : id 컬럼 뒤에 higt 컬럼을 추가한다.
> alter table user   
modify hight dec(5,2) after id;

![](https://velog.velcdn.com/images/estell/post/268eacc9-3fbe-4be5-a565-9d9fd7f5f421/image.png)

