## JOIN 조인
join은 두 개 이상의 테이블을 연결해서 하나의 결과를 만든다. 조인은 내부조인과 외부조인이 있다.
 
 
두 테이블이 일대다 관계로 연결되어야, 두 테이블을 조인 할 수 있다. 일대다 관계가 무엇인지 알아보자

---

## 일대다 관계 1 : N

![](https://velog.velcdn.com/images/estell/post/1ab6f294-8b45-4b60-ac69-71c6bd6c6ffd/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-01-22%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%206.14.01.png)

>#### 회원 테이블 1 : 구매 테이블 N 관계이다. 동일한 아이디를 통해 연결되어있다. 

테이블을 보면 동일한 아이디가 회원 테이블에서는 기본키로 구매 테이블에서는 외래키로 설정되어있다.

한 사람이 여러개의 물건을 구매할 수 있기떄문!

>- 회원 테이블 아이디 : 기본키 primary key 설정
  - 기본키 중복이 되지않고 고유한 값
- 구매 테이블 아이디: 외래키 Foreign key 설정
  - 중복 가능한 값
(구매 테이블의 기본키는 따로 있음 )


---


## 내부조인 : INNER JOIN 


내부조인은 가장 많이 사용하여 일반적으로 그냥 join이라고 부른다. 2개 이상의 테이블을 합쳐서 하나의 결과를 만든다. 

내부 조인의 문제점, 양쪽 테이블에 모두 존재하는, 조인이 되는 데이터만 조회 가능하다. 구매한 회원의 데이터만 조회되지 구매하지 않은 회원의 정보는 볼 수없다. 

> **SELECT** [조회할 열 이름]
**FROM** [1번 테이블]
**INNER JOIN** [2번쨰 테이블]
**ON** [조인 될 조건]
+옵션 : **WHERE** [조회 조건]


- 예시) member 과 buy 테이블을 mem_id를 기준으로 조인/ 합쳐서, buy 테이블의 mem_id 구매한 사람이 MMU인 경우인 행 데이터를 조회해라 
> select *  
from buy
inner join member
on buy.mem_id = member.mem_id
where buy.mem_id = 'MMU';
> - 회원테이블과 구매테이블에 있는 마마무 정보가 모두 출력됨
![](https://velog.velcdn.com/images/estell/post/88bbd250-411a-4fc4-a45a-daf76f62008a/image.png)

### 동일한 열 이름의 데이터를 조회할 경우 
다른 두 테이블에 동일한 열데이터가 있다면, 기준을 잡아줘야한다.

> **SELECT** 테이블명.[조회할 열이름]
select buy.mem_id 
select member.mem_id

- 예시)  기준을 buy 구매 테이블의 mem_id로 조회함 member을 기준으로 해도 동일
> select buy.mem_id, mem_name, prod_name, addr, concat(phone1, phone2) AS '연락처'
from buy
inner join member
on buy.mem_id = mem  
![](https://velog.velcdn.com/images/estell/post/302630d5-b02c-47f3-a64c-744b52b9cf68/image.png)


### 결과는 동일하지만 정확하게 조회할 열 지정해주는게 더 좋다.
동일한 열이름이라 기준을 잡아줬지만, 
사실 조인했을경우 어느쪽 테이블의 열 데이터인지 정확하게 구분해주는 것이 좋다.

>SELECT 테이블 + . + 열이름
select buy.mem_name, buy.prode_name, ....


## 테이블명 별칭 활용 
정확하게 지정해 주는 것은 좋은데, 조회할 열데이터가 많을 경우 sql문이 너무나 길어진다.

이럴경우 별칭을 사용해준다. 예시는 아래 외부조인에서 살펴보자

>SELECT [테이블 지칭별칭][.][열이름],...
**FROM** [1번째 테이블명] 띄어쓰기 [별칭]
**INNER JOIN** [2번쨰 테이블] 띄어쓰기 [별칭]


---

## 외부 조인 : OUTER JOIN
외부조인은 두 테이블을 조인할때 데이터가 한 쪽 테이블에만 존재해도 결과를 조회할 수 있다. 
(자주 사용되지는 않지만, 필요한 경우 사용한다.)

어떤 테이블을 기준으로 조인할건지에 따라서, 왼쪽 **LEFT, 오른쪽 RIGHT, 모든 FULL** 조인 3가지로 구분되며 LEFT를 가장 많이 사용한다. 

이때 기준으로 잡은 테이블의 데이터는 모두 조회한다.
 

> **SELECT** [조회할 열 이름]
**FROM** [LEFT 테이블(1번 테이블)]
**[LEFT : RIGHT : FULL] + JOIN** + [LIGHT 테이블(2번 테이블)]
**ON** [조인 될 조건]
+옵션 : **WHERE** [조회 조건];

#### member 테이블을 기준으로 조회해본다면?

- LEFT JOIN 예시): 왼쪽 member 테이블을 기준 조회
> 
select M.mem_id, M.mem_name, B.prod_name, M.addr
from member M
left join buy B
on M.mem_id = B.mem_id
ORDER BY M.mem_id;


#### RIGHT JOIN은 LEFT JOIN과 똑같기에 LEFT JOIN으로 사용한다.
RIGHT JOIN 사용시 기준으로 잡을 테이블의 위치만 2번째, 오른쪽에 배치하면 동일하기 떄문에, 
기준으로 잡을 테이블을 FROM 옆인 1번째 왼쪽에 배치하고 LEFT JOIN을 쓰면 된다.

- RIGHT JOIN 예시): 오른쪽 member 테이블 기준 조회
>select M.mem_id, M.mem_name, B.prod_name, M.addr
from buy B
right join member M
on M.mem_id = B.mem_id
ORDER BY M.mem_id;

- 동일한 결과 : member 테이블의 데이터는 buy 테이블에 없어도 조회된다. (회원이 구매한 물건이 없어도 조회되는 상태)
> ![](https://velog.velcdn.com/images/estell/post/cc988f70-3542-46bf-a486-5bf1f7250928/image.png)


---


* FULL JOIN mysql에서는 full outer join을 지원하지 않는다.
-> 이 부분은 union으로 해결할 수 있다고 한다. [참고한 블로그](https://wkdgusdn3.tistory.com/entry/mysql%EC%97%90%EC%84%9C-full-outer-join-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0)
