## now() vs sysDate()

둘다 현재 날짜 값을 가져온다. 하지만 '현재'의 기준이 다름.
<br>


### NOW()

- 쿼리가 수행되는 시간에 고정


### SYSDATE()

- 함수 호출 시마다 시간이 변한다.


이러한 차이를 방지하기 위해 MySQL 옵션 --sysdate-is-now(default값: false ) 을 통해 SysDate() 와 Now()가 똑같이 동작하도록 설정 가능.



참고 : <br>
https://velog.io/@kimju0913/mysql-now-%EC%99%80-sysdate%EC%9D%98-%EC%B0%A8%EC%9D%B4 <br>
https://reference-m1.tistory.com/336
