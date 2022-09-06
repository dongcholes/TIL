
## csv파일 업로드하는 writer 구현 2가지 방법

```java

// 1. FlatFileItemWriter 를 상속

import org.springframework.batch.item.file.FlatFileItemWriter;
import org.springframework.batch.item.file.transform.BeanWrapperFieldExtractor;
import org.springframework.batch.item.file.transform.DelimitedLineAggregator;
import org.springframework.core.io.FileSystemResource;
import org.springframework.stereotype.Component;

@Component
public class Writer extends FlatFileItemWriter<Employee> {

	public Writer() {
		setResource(new FileSystemResource("data/output.csv"));
		setLineAggregator(getDelimitedLineAggregator());
	}
	
	public DelimitedLineAggregator<Employee> getDelimitedLineAggregator() {
		BeanWrapperFieldExtractor<Employee> beanWrapperFieldExtractor = new BeanWrapperFieldExtractor<Employee>();
		beanWrapperFieldExtractor.setNames(new String[] {"id", "name", "salary"});

		DelimitedLineAggregator<Employee> delimitedLineAggregator = new DelimitedLineAggregator<Employee>();
		delimitedLineAggregator.setDelimiter(",");
		delimitedLineAggregator.setFieldExtractor(beanWrapperFieldExtractor);
		return delimitedLineAggregator;
		
	}
}


```java

//2. 데이터타입으로 만들고 new 연산자를 통한 변수 선언

@Bean
    @StepScope
    public FlatFileItemWriter<TestCsvFieldVo> writer() throws Exception{
        //csv파일에 작성할 데이터를 추출하기 위해서 fieldExtractor 객체가 필요
        BeanWrapperFieldExtractor<TestCsvFieldVo> extractor = new BeanWrapperFieldExtractor();
        extractor.setNames(new String[] {"id","name","address"}); //필드명 설정

        //line 구분값 설정
        DelimitedLineAggregator<TestCsvFieldVo> lineAggreator = new DelimitedLineAggregator<>();
        lineAggreator.setDelimiter(",");
        lineAggreator.setFieldExtractor(extractor);

        FlatFileItemWriter<TestCsvFieldVo> writer = new FlatFileItemWriterBuilder<TestCsvFieldVo>()
                .name("csvItemWriter")
                .encoding("UTF-8")
                .resource(new FileSystemResource("output/test.csv")) //FileSystemResource : write할때 경로 지정
                .lineAggregator(lineAggreator)
                .headerCallback(writer1 -> writer1.write("id,name,address")) //header설정
                .footerCallback(writer1 -> writer1.write("---------------\n")) //footer설정
                .append(true)
                .build();

        writer.afterPropertiesSet();

        return writer;
    }

```



