# GROUP BY

 GROUP BY는 말 그대로 그룹끼리 묶어주는 것이다.

 GROUP BY 절은 집계 함수와 함께 사용한다.  
 집계함수는 SUM(), AVG(), MIN(), MAX(),COUNT() COUNT(DISTINCT) 가 있다.
 
 또한 조건절 WHERE 이아닌 HAVING을 사용한다.
 
 
 - buy 구매 테이블  / member 회원 테이블
 
 ![](https://velog.velcdn.com/images/estell/post/c77b2210-097b-4883-a4b0-62f2a3c94164/image.png)
 ![](https://velog.velcdn.com/images/estell/post/e6fde29d-6f0c-4f41-9d2f-da9d273e044b/image.png)




 # GROUP BY + 집계함수
 
 ## SUM()
 더해주는 집계 함수
 
> **SELECT  SUM(더할 열데이터 )** + **FROM** + 테이블명 + **GROUP BY** + **그룹으로 묶어줄 기준 열 **

- 회원 id끼리 그룹을 묶어, 각 회원 그룹당 총 구매 개수 조회 ("별칭", as 별칭, 띄어쓰기 별칭)  
select mem_id "회원ID", sum(amount) "총 구매개수"   
from buy   
group by mem_id;  
![](https://velog.velcdn.com/images/estell/post/69bc30ee-d35e-4f26-b432-153ce127aa0b/image.png)


- 아이돌 그룹 id끼리 그룹을 묶어, 총 구매금액 조회 (가격 * 개수 를 곱한것을 모두 더해서 )   
select mem_id "회원ID", sum(price * amount) "총 구매금액"   
from buy   
group by mem_id;  
![](https://velog.velcdn.com/images/estell/post/6a52f391-334c-4570-aec4-dbe11cbb92b5/image.png)


 ## AVG()
 평균을 구해주는 집계 함수
 
> **SELECT AVG(평균낼 열 데이터 )**+ **FROM** + 테이블명 + **GROUP BY** + **그룹으로 묶어줄 기준 열 **

- 아이돌 그룹마다 각 평균 구매개수와, 평균 구매금액 조회
select mem_id "회원ID", avg(amount) "평균 구매개수", avg(price * amount) "평균 구매금액"
from buy   
group by mem_id;  

![](https://velog.velcdn.com/images/estell/post/90c69222-1342-429c-9850-b1cb0eeef66d/image.png)


## COUNT()
행의 개수를 세어준다.
  
> **SELECT COUNT(개수 셀 특정 열 데이터 )**+ **FROM** + 테이블명  
**SELECT COUNT(개수 셀 특정 열 데이터 )**+ **FROM** + 테이블명 + **GROUP BY** + **그룹으로 묶어줄 기준 열 **

- 모든 구매내역 개수
select count(*) from buy;
![](https://velog.velcdn.com/images/estell/post/dca4f38f-a94f-49c1-9747-0dfa10765408/image.png)

- 연락처가 있는 회원수 조회, 특정 열의 행 데이터 개수 조회  
select count(phone1) "연락처가 있는 회원 수"   
from member;  
![](https://velog.velcdn.com/images/estell/post/17f3317f-aaca-49e4-8c14-6805f8263a1c/image.png)



- 회원 명 끼리 그룹화, 연락처가 있는 회원수 조회 
select mem_id "회원명", count(phone1)  "각 회원당 갖고있는 연락처 개수"
from member 
group by mem_id;
![](https://velog.velcdn.com/images/estell/post/2214eaaa-28f9-4e9a-ade1-fa3fb791302e/image.png)



---

# GROUP BY + HAVING 조건절
>  **SELECT** + 열데이터 **FROM** + 테이블명 + **GROUP BY** + 그룹으로 묶어줄 기준 열  + **HAVING** + **조건**

- 회원 그룹끼리 각 평균 구매금액이 1000원이 넘는 그룹만 조회
select mem_id "회원ID", sum(price * amount) "총 구매금액"   
from buy group by mem_id   
having sum(price * amount)  > 1000;  
![](https://velog.velcdn.com/images/estell/post/50fe98ac-1c1c-47ff-9cee-7a81620fdf77/image.png)

- 위와 동일하나, order by 오름 차순 정렬
select mem_id "회원ID", sum(price * amount) "총 구매금액"  
from buy  
group by mem_id  
having sum(price * amount)  > 1000 
order by sum(price * amount) desc; 
![](https://velog.velcdn.com/images/estell/post/8cf0072e-fe01-41df-b2c8-57f38137b668/image.png)
