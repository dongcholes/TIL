


## InputStream

- 모래알과 같은 것. 바이트 단위로 쪼개서 그릇에 담기 좋음

- 주요 메서드 참고 (다시 정리 작성) 
https://zzdd1558.tistory.com/154


### S3 업로드 inputStream으로 넣을 때,

- ObjectMetadata 객체를 선언하여 그 크기를 specify 해야 업로드 가능하다.

```java

  // 파일의 key ,value를 넣거나
  metadata.addUserMetadata({key: 말그대로 key},{value: filename)}

  // available 함수를 통해 길이 부여
  metadata.setContentLength(inputStream.available());
  metadata.setContentType("text/csv") // csv 파일로 넣을 때

```




### InputStream 한글 깨짐현상

한글은 2~3byte인데 inputStream 바이트 단위로 쪼개므로 깨짐

Buffer 사용

https://young-ja-tmi-it.tistory.com/99





## Buffered Input/Output Stream vs 일반 Stream과 속도 비교 

참고 :
https://dog-foot-story.tistory.com/entry/Java-14-Buffered-InputOutput-Stream-%EC%9D%BC%EB%B0%98-Stream%EA%B3%BC-%EC%86%8D%EB%8F%84-%EB%B9%84%EA%B5%90
