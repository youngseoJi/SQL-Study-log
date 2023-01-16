[테이블 제약조건 기본키 , 외래키 설명](https://velog.io/@estell/SQL-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%A0%9C%EC%95%BD%EC%A1%B0%EA%B1%B4)



---

### 데이터의 무결성 보장
>**기준테이블, 참조테이블이 연결되어있는 기본키,외래키 컬럼의 데이터는 수정 및 삭제가 안된다.**


- 회원(기준테이블) 구매(참조테이블) 현재 형식
  - mem_id 키/컬럼을 통해 연관관계로 묶여있다.  
```sql
create table member 
( mem_id char(8) not null primary key,
  mem_name varchar(10) not null,
  height tinyint unsigned null
);

create table buy
(  num int auto_increment not null primary key,
   mem_id char(8) not null,
   prod_name char(6) not null,
   foreign key(mem_id) references member (mem_id)
);
```
>![](https://velog.velcdn.com/images/estell/post/6000331a-d771-4f20-b032-5e870f161e49/image.png)![](https://velog.velcdn.com/images/estell/post/b6950a47-ec49-49aa-914a-49594f9664b0/image.png)

---

## 연관관계인 기본키/외래키인 컬럼 수정 및 삭제 불가능

- **오류발생코드 ** 



```sql
update member set mem_id = "BLK" where mem_id="est";
update buy set mem_id = "BLK" where mem_id="est";

delete from member where mem_id='est'
delete from buy where mem_id='est'
```

>mem_id로 두 테이블이 묶여있어서, 수정 변경이 안된다. 
-> 반대로도 마찬가지지만, 각각 테이블에서 따로 연관관계 키/컬럼의 데이터를 변경하여 참조테이블에서 기존테이블에서 mem_id로 데이터를 조회하면 서로 데이터조회가 안되면 안된다.




> BUT 변경 가능한 방법도 있다!
[변경하는 방법](https://velog.io/@estell/SQL-%EA%B2%B0%ED%95%A9JOIN%EB%90%9C-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%97%B0%EA%B4%80%EA%B4%80%EA%B3%84-%EA%B8%B0%EB%B3%B8%ED%82%A4-%EC%99%B8%EB%9E%98%ED%82%A4-%ED%95%9C%EB%B2%88%EC%97%90-%EB%B3%80%EA%B2%BD%EA%B0%80%EB%8A%A5-%EC%98%B5%EC%85%98-ON-UPDATE-CASCADE-ON-DELETE-CASCADE)
