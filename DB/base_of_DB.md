Database를 공부하기 위해서는 상상력이 필요하다. 거대한 데이터가 뜬구름 잡는 것처럼 복잡하게 느껴질 수 있겠지만, 상상력을 발휘해서 크고 복잡하고 위험하게 생각하며 공부해 보자. 그러면 DB의 복잡성에 공감할 수 있을 것이다. 공감을 바탕으로 이해해 보자.

1. **데이터베이스의 개념**: 데이터는 체계적으로 조직, 저장 및 관리되어야 하는 정보의 집합을 말한다. 데이터베이스는 이러한 데이터를 효율적으로 관리하기 위한 시스템이다. File - SpreadSheet - DataBase로 발전했다고 이해할 수도 있다.

2. **데이터베이스 관리 시스템(DBMS)**: 데이터베이스를 관리하기 위한 소프트웨어로, 데이터의 생성, 조회, 수정 및 삭제 등 다양한 작업을 수행할 수 있다. 대표적인 DBMS로는 MySQL, Oracle, NoSQL 등이 있다. 각각의 특징을 간단히 설명하면 아래와 같다.
- 오라클은 비싸다. 자급력 있는 기업이나 정부에서 쓰고 있다.
- MySQL은 무료고 오픈소스다. 대규모의 데이터가 생성되지만, 데이터 신뢰성은 크게 중요하지 않는 서비스에 적합한 편.
- NoSQL(예를 들어, MongoDB)은 수많은, 다양한 종류의 데이터들이 발생하는 현 시점에 관계에 모두 끼워넣을 수 없는 상황에 쓴다. 2010년부터 유행해 왔다~

3. **SQL(Structured Query Language)**: DBMS를 통해 데이터베이스와 대화할 때 사용하는 표준 언어이다. 데이터베이스에서 데이터를 검색, 추가, 수정, 삭제를 할 수 있다.

4. **테이블과 스키마**: 데이터베이스는 테이블이라는 형태로 데이터를 저장한다. 각 테이블은 여러 개의 컬럼(필드)으로 구성되어 있으며, 각 컬럼은 데이터의 속성을 나타낸다. 스키마는 데이터베이스의 구조, 즉 테이블과 관계 등의 메타데이터를 정의하는 것을 뜻한다.

5. **기본적인 SQL 명령**: DB는 표면적이 넓은 기술이다. 그렇기 때문에 중심에 자리잡고 있는 기술을 먼저 이해하는 것이 중요하다. 데이터의 입력(input)과 출력(output)이 그 기본이 된다. 데이터 입력(input)에는 데이터 삽입(INSERT), 데이터 수정(UPDATE), 데이터 삭제(DELETE)가 있다. 그리고 데이터의 출력(output)에는 데이터 조회(SELECT)가 있다. 위 4가지 작업이 우리에게 필요한 것의 거의 모든 것이다. 이 네 가지 작업을 CRUD라고 부른다.