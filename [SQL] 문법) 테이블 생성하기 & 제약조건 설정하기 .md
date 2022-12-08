## 테이블을 생성하기 (use로 지정한 데이터베이스 내에)

- 테이블을 생성시 테이블 이름, 컬럼 목록과 각 컬럼의 타입을 명시해야 합니다.
- 자료형 지정: 컬럼에 저장될 데이터 자료형 타입(수, 문자, 어떤 타입이든상관없다 등을 지정)을 의미합니다.
- 제약 설정 : 컬럼에 어떤 조건,제약을 설정하는 것이다. (값이 없어도 된다, 꼭 있어야된다 등)

### 테이블 생성하기 (제약넣기)
- create 명령어로 테이블을 생성한다.

> CREATE TABLE 테이블 명;

>CREATE TABLE user (
  id int AUTO_INCREMENT PRIMARY KEY, 
  user_name varchar(10) NOT NULL,
  user_email varchar(20) UNIQUE NOT NULL,
  age TINYINT UNSIGNED DEFAULT 0
);
![](https://images.velog.io/images/estell/post/a523bd29-dee6-4c59-9980-da035399f025/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-03-07%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%205.34.20.png)

|제약|설명|
|---|---|
| AUTO_INCREMENT | 새 행 생성(행 데이터가 추가될 때 마다) 자동으로 1씩 증가|
| PRIMARY KEY | 중복 입력 불가, NULL(빈 값) 입력 불가(무조건 값이 있어야함)|
|FOREIGN KEY | 필수 X, 참조|
| UNIQUE | 중복 입력 불가|
| NOT NULL | NULL(빈 값) 입력 불가(무조건 값이 있어야함)|
| UNSIGNED | (숫자일시) 양수만 가능|
| DEFAULT | 값 입력이 없을 시 기본값|

## PRIMARY KEY, FOREIGN KEY의 차이

### 💡PRIMARY KEY 
- 각 테이블에 한개만 지정 가능하다 => 각 테이블을 나타내는 id 같은 것
- 기본으로 인덱스 생성
  (예를들어, 책의 색인처럼 각 번호로 데이터를 빠르게 찾을 수 있다.)
- 보편적으로 AUTO_INCREMENT와 함께 사용한다. 

### 💡FOREIGN KEY
- 각 테이블에 여러개가 지정 가능하다.
- 테이블 간의 링크를 걸어준다.
A FOREIGN KEY는 다른 테이블에서 참조하는 한 테이블의 필드(또는 필드 모음)이다. 


=> [데이터 자료형](https://velog.io/@estell/SQL-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EC%9E%90%EB%A3%8C%ED%98%95%EC%97%90-%EB%8C%80%ED%95%B4-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90)
=> [테이블에 데이터 입력하기](https://velog.io/@estell/SQL-%EB%AC%B8%EB%B2%95-%ED%85%8C%EC%9D%B4%EB%B8%94-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EC%B6%94%EA%B0%80%EC%82%AD%EC%A0%9C-%EC%88%98%EC%A0%95-%EB%B0%A9%EB%B2%95-INSERT-INTO-DELETEUPDATE-SET)


> [참고페이지 MYSQL 자료형부분](https://dev.mysql.com/doc/refman/8.0/en/date-and-time-types.html)
