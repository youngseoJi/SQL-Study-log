

## 데이터 형변환

데이터의 형변환이란, 문자형을 정수형으로 또는 반대로 변경하는 것을 말한다. 형변환은 결과는 똑같지만 변환방법에 따라 명시적, 암시적 형변환으로 나눠진다.

### 명시적 형변환
CASE 함수를 사용하여 형변환한다.

>**CASE ( 값 AS 데이터 형식(길이)) ** 
**CONVERT( 값, 데이터 형식(길이))**



- 예시 1) 실수형 -> 정수형
테이블) 블랙핑크가 구매한 기존 평균구매가:  **실수형 360.0000 ** -> **정수형 360 으로 변환**

>select mem_id, **CAST(avg(price) as signed)** '평균 구매가' from buy where mem_id = 'BLK';
>
>select mem_id, **CONVERT (avg(price), signed)** '평균 구매가' from buy where mem_id = 'BLK';
>
>- 정수형으로 형변환된 결과
![](https://velog.velcdn.com/images/estell/post/0fb609cd-55c4-4a24-ae62-4ba5b90a09d8/image.png)

-  예시 2) '문자형' -> data 날짜 형식 
>select cast('2022/12/15' as date) '날짜형식';
>select convert('2022%12%15', date) '날짜형식';
> - DATE 형식으로 변환된 결과
![](https://velog.velcdn.com/images/estell/post/ac4bc4c4-c798-43e9-9821-a08e189fe615/image.png)


## 암시적 형변환
직접 형변환을 지정을 하지 않아도 자연스럽게 형변환이 되는 것이다.
(연산과 연결CONCAT 인한 형변환)

- CONCAT : 문자열로 연결해준다. 이때 정수형과 문자형이면 문자를 정수를 변환하여 연결한다.
>**CONCAT** (값 + 값)
>
> 값 + 연산기호 + 값 

- CONCAT 형변환 예시) 문자로 형변환
> - 문자 외 믄자 연결 : 문자 '100200'
select concat('100', '200');
![](https://velog.velcdn.com/images/estell/post/93e39699-dc23-4b83-9a8b-ea15af3ed8d3/image.png)
> -  정수와 문자를 연결 (정수가 문자로 변환 ) : 문자 100200
select concat(100, '200');
![](https://velog.velcdn.com/images/estell/post/0bc49b67-c5d6-4209-9ce2-501ad48b8af5/image.png)


- 연산 형변환 예시) 정수로 형변환
>- 문자 + 문자 : 정수로 변환 되어 연산 300
select '100' + '200' ;
![](https://velog.velcdn.com/images/estell/post/6394d794-fe09-4240-a5e3-8044962d3e77/image.png)
> - 정수인 2로 변환 비교
select 1 > '2mega'; 
![](https://velog.velcdn.com/images/estell/post/cd1e80f0-144c-4ce8-9883-6d9d99b5d8e7/image.png)
>
> - 문자는 0으로 변환
select 0 = 'mega2';
![](https://velog.velcdn.com/images/estell/post/a8778034-611e-4d85-8b77-48ec7d12aeec/image.png)
