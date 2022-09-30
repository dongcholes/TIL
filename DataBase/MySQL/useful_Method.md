
# Useful Methods from MYSQL


### SUBSTRING(string, start, length)

SELECT SUBSTRING(value, 1, 1) AS column_name; 으로 사용 (첫글자만)  

> 주의! java의 substring은 index 0부터 시작. mysql은 1로 시작

<br><br>
혹은,<br> 
SUBSTRING(string FROM start FOR length)

<br><br>

출처 : https://www.w3schools.com/sql/func_mysql_substring.asp



<br><br><br>

### CAST( {data} AS {dataType} )

CONVERT 함수로도 사용할 수 있음.

참고 : https://ponyozzang.tistory.com/653



<br><br><br>

### CONCAT(str , str, str)
