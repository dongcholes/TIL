

## carriage return 에 대한 해결

String에 carriage return(개행문자)이 들어가 있을때 해결방법


```java

s = s.replaceAll("\\n", "");
s = s.replaceAll("\\r", "");

```

<br><br>
혹은
<br><br>

```java

s = s.replaceAll("\\s{2,}", " ");

```

참고 : <br>
https://stackoverflow.com/questions/10499005/how-to-remove-a-carriage-return-from-a-string
