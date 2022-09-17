
## DateTimeFormatter


```java

//example
 LocalDate date = LocalDate.now();
 String text = date.format(formatter);
 LocalDate parsedDate = LocalDate.parse(text, formatter);

//return String 


```


```java
//example 2
currentDateTime = LocalDateTime.now();
currentDateTime.format(DateTimeFormatter.ofPattern("yyyy-MM-dd");  // String 타입의 날짜

```





참고 : https://docs.oracle.com/javase/8/docs/api/java/time/format/DateTimeFormatter.html
