

# hashcode()와 equals() 함수 정리 


## 개요

equals()와 hashcode() 함수는 Object class에 정의되어 있다. 모든 JAVA 객체는 Object 객체의 자식이므로 두 함수를 상속받고 있다.



<br><br><br>

## equals() 함수란?

<br>

1. boolean equals(Object obj) 로 정의된 equals 함수는 객체의 주소값을 비교하므로 같은 메모리 주소의 객체를 참조해야만 true 를 리턴한다.
<br>
( => 값이 같더라도 저장된 메모리 주소가 다르면 false 리턴)

```java

public boolean equals(Object obj) {
    return (this == obj);
}

```


<br>

2. String을 비교 시, String class에서 override한 equals 함수를 사용한다. String class의 equals 함수는 메모리에 저장된 문자열의 값이 같은지 비교하는 코드가 추가되었다.

<br>

  String 변수를 선언하면 서로 다른 메모리 주소에 저장이 되지만(즉, 서로 다른 객체), String class에서 override 한 equals 함수를 통해 비교하면 저장된 문자열의 값이 같으면 true를 리턴한다. 

```java

String s1 = new String("Test");
String s2 = new String("Test");

System.out.println(s1 == s2);			// false
System.out.println(s1.equals(s2));		// true;

// equals, overridden in String Class 
public boolean equals(Object anObject) {
    if (this == anObject) {
        return true;
    }
    if (anObject instanceof String) {
        String anotherString = (String)anObject;
        int n = value.length;
        if (n == anotherString.value.length) {
            char v1[] = value;
            char v2[] = anotherString.value;
            int i = 0;
            while (n-- != 0) {
                if (v1[i] != v2[i])
                    return false;
                i++;
            }
            return true;
        }
    }
    
    return false;
}


```
  

<br><br><br>

## hashcode() 함수는?


참고 : 
https://www.baeldung.com/java-hashcode
