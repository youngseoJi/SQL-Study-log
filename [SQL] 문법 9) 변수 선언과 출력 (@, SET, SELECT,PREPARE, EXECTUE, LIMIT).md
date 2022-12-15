## 변수 
sql도 변수를 선언하고 사용할 수 있다. 임시저장소, 이후 다른 사람이 접속 또는  sql 종료 후 실행하면 날라간다. test용도

 
 
## 변수의 선언과 출력 : SET, SELECT
- **SET** : 변수의 선언 및 초기화
- **SELECT** : 변수 조회/출력_텍스트_


> **SET @변수이름 = 변수의 값**
>**SELECT @변수이름**

- 예시) 
>set @txt = '가수 이름 => ';
set @height = 166;
select @height;
![](https://velog.velcdn.com/images/estell/post/2ba01073-2086-4093-92a6-5d48504e0b38/image.png)

### 조건문 사용하여 변수 츨력 
조건문 where, 연산자, LIMIT등 으로 특정 데이터를 출력할 수 있다.

- 예시 ) 변수에 지정한 166키보다 큰 키인, 가수를 출력 
>select @txt, mem_name from member where height > @height;
![](https://velog.velcdn.com/images/estell/post/78f487fc-cf3d-4f2b-9401-7823f0226561/image.png)

이 중에, LIMIT 제한조건은 변수에 지원되지않는 문법이 이라 PREPARE, EXCUTE를 사용해야 변수와 함께 사용할 수 있다. 
- 에러가 나는 문법 -> 정상적으로 사용하는 방법은 아래에
> set @count = 3;
select mem_name, height from member order by height LIMIT @count;

---

## 변수에 지원되지 않은 문법 사용방법

- **PREPARE** : 변수의 선언 및 출력준비, 'sql;문을 전달받아 변수의 출력 준비만 한다.
- **?** : 변수의 값을 모름으로 표시한다.
- **EXCUTE** : 변수의 출력, PREPARE 준비해둔 sql문에 USEING 뒤에 있는 @변수명을 ?에 대입하여 출력한다.


> **PREPARE** 지정이름 **from** 'sql문 + **?**'

> **EXCUTE** 지정이름  **USEING @**변수명;



- prepare 예시) MYSQL 이라는 변수 선언 -> SELECT 'sql'문 -> 회원의 키를 '?' 어떤 변수 만큼 출력준비해달라  
>prepare mySQL from 'select mem_name, height from member order by height LIMIT ?';
>
- execut 예시) mySQL 변수 실헹 -> @count 변수에 선언된 3을 '?' 에 대입하여 'select문을 실행해라' 
>execute mySQL using @count;
![](https://velog.velcdn.com/images/estell/post/3e8e22a4-3526-419c-88a0-5b97aec1166f/image.png)

