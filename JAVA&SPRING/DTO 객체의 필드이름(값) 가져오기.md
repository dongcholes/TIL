


## DTO 객체의 필드이름(값) 가져오기




```java

StringBuilder initialContent = new StringBuilder();
int count = 0;

//필드 이름 갖고오기 (header)
StringBuilder header = new StringBuilder();
DtoObj fieldName = new DtoObj();

for(Field field : fieldName.getClass().getDeclaredFields()) {
  field.setAccessible(true);
  if(header.length() != 0{
    header.append(separator);   //구분자 : 쉼표(,)
  }
   header.append(field.getName().toUpperCase());  // 엑셀 등의 데이터로 출력 시 요청 양식에 따라 header를 대문자 혹은 소문자로 변경
}
initialContent.append(header).append("\n");

//내용 작성 (한 행씩)
for(DtoObj dtoObj : dtoObjList){
  count++;
  dtoObj.setCol1(count);  // 몇번째 데이터인지 기록하는 컬럼이 있다면 count 통해 추가
  StringBuilder oneRow = new StringBuilder();
  
  for(Field field : dtoObj.getClass().getDeclaredFields()) {
    filed.setAccessible(true);
    Object value = field.get(dtoObj);

    if(field.getName().equals()){     // 필드 별 커스텀 설정
    
     ...   
    }
    if(oneRow.length != 0){
      oneRow.append(separator);   //구분자
    
    }
    oneRow.append(value);
  
  }
  initialContent.append(oneRow).append("\n");
}
initialContent.append("TOTAL:").append(count);  //마지막 행에 토탈 갯수 추가해주고 싶으면 count 활용 추가

InputStream targetStream = new ByteArrayInputStream(initialContent.toString().getBytes()); // String화해서 바이트 단위로 쪼개어 inputStream으로 바꿈 
dataUploader.fileProcess(targetStream, table_name);   // 파일업로드 메서드 호출해서 inputStream 타입의 데이터 업로드


```
