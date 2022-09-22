


CREATE TABLE TEMP_테이블명(

 

)

 

INSERT TEMP_테이블

SELECT * FROM 원본테이블

 
 
 
 ### to SELECT INTO
 
 select * into TEMP_테이블 from 원본테이블 [조건문]

 
 만약 임시테이블을 생성하여 복사하고 싶다면

 

select * into #TEMP_테이블 from 원본테이블 [조건문]

 

#을 붙여주면된다. 

##을 붙이면 전역 임시테이블로 생성되면

#은 해당 세션에서만 사용가능하며

##은 전역으로써 모든 세션에서 사용 가능하다.


출처 : https://dreaming-soohyun.tistory.com/entry/MSSQL-SELECT-INTO-%ED%85%8C%EC%9D%B4%EB%B8%94-%EB%98%90%EB%8A%94-%EC%9E%84%EC%8B%9C%ED%85%8C%EC%9D%B4%EB%B8%94-%EB%B3%B5%EC%82%AC
