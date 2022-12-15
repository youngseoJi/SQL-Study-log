> sql 복습 겸/ 과거 정리 글 보강하여 재업로드 중 


## 테이블 조회 

### 현재 사용 중인 DB의 테이블 목록 조회하기
> **SHOW TABLES**;
![](https://images.velog.io/images/estell/post/8ac3679b-f74a-479c-b14d-9499270a2cba/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-03-07%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%209.20.37.png)

### 현재 데이터베이스에 존재하는 모든 테이블 정보보기
> **SHOW TABLE STATUS**;
![](https://images.velog.io/images/estell/post/597e570d-34e6-4e1f-9a8c-686e5878dd10/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-03-07%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%209.22.01.png)

### 특정 테이블의 구조를 조회 하기
>**DESCRIBE** 테이블명;
**DESC** 테이블명;

- describe user;
  => user 테이블의 구조를 조회한다. (행을 구별하는 열은 무엇인지, 데이터 타입이 무엇인지 등)
  ![](https://images.velog.io/images/estell/post/b56083e1-619d-452b-a943-c6cb09bb023c/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-03-07%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%209.22.57.png)
