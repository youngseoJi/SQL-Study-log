[결합된 테이블의 연관관계 기본.외래키 변경불가능 ](https://velog.io/@estell/sql-%EC%A0%9C%EC%95%BD%EC%A1%B0%EA%B1%B4)

원래는 불가능 하지만, 가능하게 해주는 옵션이 있다.

---

## 테이블의 연관관게 기본/외래키 수정 및 삭제 가능 옵션
ON UPDATE/DELETE CASCADE 은 결합된 기준 테이블과 참조 테이블의 연관관계 기본/외래키를 자동으로 연결하여 한번에 변경해줄 수 있다.


>**ON UPDATE CASCADE  
ON DELETE CASCADE**


- 예시) 테이블을 변경하는 ALTER 문을 사용,  ADD CONSTRAINT 옵션으로 외래키를 지정한 후
옵션 두개를 ON UPDATE/DELETE CASCADE 추가하면 수정 삭제가 가능하게 된다.

>ALTER TABLE 테이블 
ADD CONSTRAINT (참조테이블 외래키 컬럼명) REFERENCES 테이블명 (기준테이블 기본키 컬럼명)
**ON UPDATE / DELETE CASCADE **



```sql
create table buy
(  num int auto_increment not null primary key,
   mem_id char(8) not null,
   prod_name char(6) not null
);
```
```sql
alter table buy   
add constraint 
foreign key(mem_id) references member (mem_id)
on update cascade
on delete cascade;
```
![](https://velog.velcdn.com/images/estell/post/1fa44705-b2cf-402a-ae4b-834db5a97540/image.png)

---
## 수정 및 삭제 가능

- 기존 테이블 상태
  update / delete 수정 삭제가 기존에는 불가능 했지만, 테이블에 위의 옵션을 추가하면서 수정삭제가 가능해진 상태  아래에 수정 결과, 삭제 결과와 확인.
>![](https://velog.velcdn.com/images/estell/post/f41c2629-0fe7-4812-b3a0-bde5ceaeeaba/image.png)![](https://velog.velcdn.com/images/estell/post/62ec4a0b-5564-440d-89b9-ffb600371b83/image.png)

- 수정 및 삭제
"est" mem_id가 기준, 참조 테이블에서 연결되어 한번에 수정 및 삭제 된다. 
>- 수정
update member set mem_id = "BLK" where mem_id="est";
![](https://velog.velcdn.com/images/estell/post/76ca5855-2fd5-4879-afe3-9347f6a8bd3f/image.png)![](https://velog.velcdn.com/images/estell/post/40c1e860-32a0-41c3-ba1a-aae444d4fff1/image.png)
>- 삭제
delete from member where mem_id='BLK';
>![](https://velog.velcdn.com/images/estell/post/dc560a80-b022-4f1c-bc4d-1833c886c337/image.png)![](https://velog.velcdn.com/images/estell/post/6245c191-c270-418a-9e48-7ac375e133ec/image.png)



>수정 및 삭제가 잘 된 것을 볼 수 있다.
