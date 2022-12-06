# SQL

## 내장함수

#### NULL 값 처리

- NULL 값?

  - 아직 지정되지 않은 값

  - NULL값은 '0', ' '(빈문자), ' '(공백) 등과 같이 특별한 값

  - NULL값은 비교 연산자로 비교가 불가능함

  - NULL값의 연산을 수행하면 결과 역시  NULL 값으로 반환된다.

- 집계 함수를 사용할 때 주의할 점

  - ‘NULL+숫자’ 연산의 결과는 NULL

  - 집계 함수 계산 시 NULL이 포함된 행은 집계에서 빠짐

  - 해당되는 행이 하나도 없을 경우 SUM, AVG 함수의 결과는 NULL이 되며, 
     COUNT 함수의 결과는 0.

    

    

    <img src="C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20221205112621434.png" alt="image-20221205112621434" style="zoom:50%;" />

<img src="C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20221205112638771.png" alt="image-20221205112638771" style="zoom:50%;" />





- NULL값 확인하는 방법 

  - is NULL / is not NULL

    =가 아닌 is null을 사용해서 찾는다.

- IFNULL 
  - NULL값을 다른 값으로 대치하여 연산하거나 다른 값으로 출력
  - ifnull(속성, 값) - 값에는 문자도 가능.



SELECT  name ‘이름’, IFNULL(phone, '연락처없음') ‘전화번호’

FROM  Customer;

<img src="C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20221205113122757.png" alt="image-20221205113122757" style="zoom:33%;" />