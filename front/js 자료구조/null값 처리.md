

## false로 처리되는 경우


### 0, '', null, undefined

<br><br>

## Nullish Coalescing (??)
<br>
 
``` javascript

  var a = null;
  var b = undefined;
  var c = 0;
  var d = '' ;

  a ?? 1    // 1
  b ?? 2    // 2
  c ?? 3    // 0
  d ?? 4    // ''

``` 

<br><br>
Nullish Coalescing 연산자는 오로지 null, undefined 처럼 값이 정의되지 않는 항목에 대해서만 동작
