
# ArrayList.removeAll() vs clear()

- List 객체의 모든 요소를 제거한다는 점에서 동일


## removeAll()

```java

// removeAll() 의 내부 소스코드

public boolean removeAll(Collection<?> c) {
    boolean modified = false;
    Iterator<?> e = iterator();
    while (e.hasNext()) {
        if (c.contains(e.next())) {
            e.remove();
            modified = true;
        }
    }
    return modified;
}


```

- c.contains() 는 indexOf() 를 호출

```java

 public boolean contains(Object o) {
    return indexOf(o) >= 0;
 }

```


- indexOf() 를 통해 List의 모든 요소들을 도면서 해당 원소가 있는지 계속 검사 



## clear()

- ArrayList 객체의 모든 요소를 제거




## 차이점

- removeAll() method는 Collection 타입의 인수가 존재하고, 메서드를 호출한 컬렉션 객체와 인자로 전달된 컬렉션 객체를 비교하여 일치하는 요소를 제거하므로 시간이 더 많이 소요. 


<br><br><br>


참고 :  <br><br>

https://stackoverflow.com/questions/7032070/what-is-the-difference-between-arraylist-clear-and-arraylist-removeall    <br>
https://developer-talk.tistory.com/479    <br>
https://codingdog.tistory.com/entry/java-list-removeall-vs-clear-%EC%96%B8%EC%A0%9C-%EC%93%B0%EB%8A%94%EC%A7%80-%EC%A0%95%ED%99%95%ED%95%98%EA%B2%8C-%EC%95%8C%EC%95%84%EB%B4%85%EC%8B%9C%EB%8B%A4
<br>
