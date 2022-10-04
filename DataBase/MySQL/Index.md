
# INDEX 개념

- INDEX란 책의 목차와 같은 개념으로, 데이터를 보다 효율적이고 빠르게 색인하기 위한 것. <br>
- INDEX가 없다면 full-scan한다. 

<br><br><br>


## INDEX의 자료구조

### 1. Hash Table

![image](https://user-images.githubusercontent.com/74232355/186689375-e015337b-4662-417b-b8b7-dccba3cdb1ba.png)


- Key-Value 로 이루어진 데이터를 저장하는데 특화된 자료 구조 
- 특정 컬럼의 값과 데이터의 위치를 key-value로 사용
- '버켓' 이라는 배열 존재
- 해시함수를 통해 Key를 고유한 해시값으로 변환하여 버켓 배열의 index로 사용
- 평균적인 시간 복잡도는 O(1)로 매우 빠른 검색 지원 
- 해시 함수를 제대로 정의하지 않으면 해시함수를 통해 산출한 해시 값이 중복되는 '해시 충돌' 이 발생
- 해시 충돌 발생 시 검색 성능이 하락해 시간복잡도가 O(N)에 수렴할 수도 있다.

- 해시테이블 사용하는 경우 매우 제한적
- key가 조금이라도 다르면 완전히 다른 해시 값 생성하므로 where = (등호) ~~ 연산에서 효율 좋지만 , 부등호 연산은 부적합
- 해시 테이블은 내부 데이터들이 정렬되어 있지 않아 탐색이 비효율적


### 2. B- Tree

![image](https://user-images.githubusercontent.com/74232355/186691866-7fa45cb1-1b07-4164-821c-c8bc1e254358.png)

- 자식노드가 2개 이상인 트리 
- 이진검색 트리처럼 각 Key의 왼쪽 자식은 항상 key보다 작은 값을 오른쪽 자식은 큰 값을 가진다.
- 특정 컬럼 값(Key)에 해당하는 노드에 데이터의 위치(Value)를 저장
- B-Tree 내부 동작 구조 차후 정리 (https://velog.io/@emplam27/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EA%B7%B8%EB%A6%BC%EC%9C%BC%EB%A1%9C-%EC%95%8C%EC%95%84%EB%B3%B4%EB%8A%94-B-Tree)

- B-Tree의 Key-Value 값들은 항상 Key를 기준으로 오름차순 정렬
- 부등호 연산(>, <)에 대해 해시 테이블보다 효율적인 데이터 탐색이 가능
- B-Tree는 균형 트리(Balanced Tree)로서, 최상위 루트 노드에서 리프 노드까지의 거리가 모두 동일하기 때문에 평균 시간 복잡도는 O(logN)



- Index가 적용된 테이블에 데이터 갱신(INSERT , UPDATE, DELETE)가 반복되면서 트리의 균형이 깨지면 성능이 악화된다.

### 3. B+ Tree

B+ Tree 는 모든 노드에 value를 저장하는 BTree와 다른 특성을 갖고 있다.
- 리프노드만 인덱스 + 데이터(value), 나머지 노드들은 데이터를 위한 Index(key)만 가짐.
- 리프노드는 LinkedList로 연결
- 데이터 노드는 크기는 인덱스 노드의 크기와 같지 않아도 된다.
- 인덱스 컬럼에서 부등호를 사용하는 순차검색이 빈번하게 일어나기 때문에 BTree의 리프노드들을 LinkedList로 연결하여 순차검색을 용이하게 함.
-  Best Case에 대해 리프노드까지 가지 않아도 탐색할 수 있는 BTree에 비해 무조건 리프노드까지 가야한다는 단점
-  비록 B+Tree는 O(log2n) 의 시간복잡도를 갖지만 해시테이블보다 인덱싱에 더욱 적합한 자료구조




![image](https://user-images.githubusercontent.com/74232355/193821108-e9562f75-1f2a-4912-9bd0-0cbbb3d2a487.png)



참고 : <br>
https://tecoble.techcourse.co.kr/post/2021-09-18-db-index/ <br>
https://mangkyu.tistory.com/96
