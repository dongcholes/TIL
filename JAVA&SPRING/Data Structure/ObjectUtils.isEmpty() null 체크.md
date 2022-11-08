
# ObjectUtils.isEmpty() null 체크

```java

public class MainApp{
  
  public static void main(String[] args) {
    
    Object object = null;
    System.out.println(ObjectUtils.isEmpty(object));        // true
    
   
    object = "";
    System.out.println(ObjectUtils.isEmpty(object));        // true
      
    
    object = new String[]{ };
    System.out.println(ObjectUtils.isEmpty(object));        // true
    
    
    object = new Object();
    System.out.println(ObjectUtils.isEmpty(object));        // false
    
    
    object = 123;
    System.out.println(ObjectUtils.isEmpty(object));        // false 
    
   
    object = "123";
    System.out.println(ObjectUtils.isEmpty(object));        // false
  }
}



```




<br><br>

참고 : https://blog.naver.com/PostView.nhn?isHttpsRedirect=true&blogId=seek316&logNo=222355031997&categoryNo=42&parentCategoryNo=0&viewDate=&currentPage=1&postListTopCurrentPage=1&from=postView
