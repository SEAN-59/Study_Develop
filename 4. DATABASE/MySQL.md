# MySQL

## 명령어 분류
### DDL : 데이터 정의어
- DB나 Table 생성, 삭제하거나 구조 변경 위한 명령어
```
1. CREATE   | 생성 | DB 오브젝트 생성
2. ALTER    | 변경 | DB 오브젝트 변경
3. DROP     | 삭제 | DB 오브젝트 삭제
4. TRUNCATE | 삭제 | DB 오브젝트의 내용 삭제
```

### DML : 데이터 조작어
- DB에 저장된 데이터 처리하거나 조회, 검색하기 위한 명령어
```
1. INSERT | 삽입 | 신규 데이터를 테이블에 저장
2. UPDATE | 수정 | 테이블의 내용을 수정
3. DELETE | 삭제 | 테이블의 내용 삭제
4. SELECT | 조회 | 테이블의 내용 조회
```

### DCL : 데이터 제어어
- 무결성 유지 하며 내부 규정이나 제약 조건 기술 위한 명령어
```
1. GRANT  | DB 사용자에게 권한 부여
2. REVOKE | DB 사용자에게 권한 회수
```

### 기본적인 용어
1. 테이블 : 서로 연관된 데이터의 집합
2. 튜플 = 레코드 = 컬럼 : 하나의 단위로 취급되는 자료의 집합, DB에서 행에 해당 = 관계된 데이터의 묶음
3. 필드 = 속성(attribute) : 가장 작은 단위의 데이터, DB에서 열에 해당 = 자신만의 타입을 가짐

---
## 문법
### 데이터 베이스
```SQL
1. DB 조회
    SHOW DATABASES; 
2. DB 사용
    USE <DB_NAME>;
3. DB 생성
    CREATE <DB_NAME>;
4. DB  삭제
    DROP DATABASES <DB_NAME>;
```

---
### 테이블
1. 정의
```SQL
CREATE TABLE <TABLE_NAME>(
    <FIELD_NAME> <TYPE>(<자리수>) <조건> 
    PRIMARY KEY(<PK 지정한 FIELD_NAME>)
);

e.g.
CREATE TABLE testtable(
    id varchar(10) NOT NULL,
    password int(10) NOT NULL,
    count int(10) unsigned NOT NULL default '0',
    PRIMARY KEY (id)
);
```

2. 제약 조건
- 무결성을 지키기 위해 데이터 입력시 실행되는 규칙
```
CREATE TABLE 문에서 사용 할 수 있는 조건
1. NOT NULL     | 해당 필드 NULL 값 불가
2. UNOQUE       | 해당 필드는 서로 다른 값을 가져야 함
3. PRIMARY KEY  | 기본키 : 1,2 의 특성 전부 가짐
4. FOREIGN KEY  | 외래키 : 하나의 테이블이 다른 테이블에 의존
5. DEFAULT      | 해당 필드의 기본값 설정
```

3. 다른 것들
```SQL
1.  테이블 정보 조회
    DESCRIBE <TABLE_NAME>; 
2. 테이블 삭제
    DROP TABLE <TABLE_NAME>;
3. 테이블 수정
    ALTER TABLE <TABLE_NAME> ADD COLUMN <FIELD_NAME> <TYPE> <조건>;
    ALTER TABLE <TABLE_NAME> MODIFY COLUMN <FIELD_NAME> <TYPE> <조건>;
    ALTER TABLE <TABLE_NAME> DROP COLUMN <FIELD_NAME> <TYPE> <조건>;
    ALTER TABLE <TABLE_NAME> RENAME <TABLE2_NAME>;
```

### 레코드
    - 뒤에 WHERE <조건> 은 필요하면 언제든 붙여도 됨
    - <FIELDS_NAME> 은 필드들의 이름을 써도 되고 * 로 전체라고 해도 된다.
```SQL
1. 조회
    - <TABLE>의 모든 데이터(*) 조회
    SELECT * FROM <TABLE_NAME>; 

    - <TABLE> 내에서 <조건>과 일치하는 레코드 조회
    SELECT <FIELDS_NAME> FROM <TABLE_NAME> WHERE <조건>; 

    - <TABLE> 내에서 <조건>으로 정렬해서 레코드 조회
    SELECT <FIELDS_NAME> FROM <TABLE_NAME> ORDER BY <조건>; 

    - <FIELD> 를 기준을으로 중복된 레코드 제거
    SELECT DISTINCT <FIELD_NAME> FROM <TABLE_NAME>;

e.g.
    - DB의 table에서 b가 A로 시작하는 레코드들의 a, b 필드 조회
    SELECT a, b FROM DB.table WHERE b LIKE 'A%';
    - table 에서 c 필드의 값이 10인 레코드 개수
    SELECT COUNT(*) FROM table WHERE c = '10';


2. 추가
    - 테이블에 새 레코드 추가
    INSERT INTO <TABLE_NAME> (FIELD1_NAME, FIELD2_NAME) VALUES (FIELD1_VALUE, FIELD2_VALUE);

    - 모든 필드를 FROM에서 TO로 복사
    INSERT INTO <TO_TABLE_NAME> SELECT * FROM <FROM_TABLE_NAME>;

    - 지정 필드를 복사
    INSERT INTO <TO_TABLE_NAME> (FIELD1_NAME, FIELD2_NAME) SELECT <FIELD1_NAME>, <FIELD2_NAME>, <FIELD3_NAME> FROM <FROM_TABLE_NAME>;

3. 수정
    UPDATE <TABLE_NAME> SET <FIELD1_NAME>=<FIELD1_VALUE>, <FIELD2_NAME>=<FIELD2_VALUE> WHERE <조건>;

4. 삭제
    DELETE FROM <TABLE_NAME> WHERE <조건>;
```

---
### 조인 (JOIN)
    1. 하나의 테이블에서 원하는 데이터가 다 있을 수 있지만 두 테이블을 엮어야 결과가 나오는 경우 사용
    2. 두 테이블을 조인하기 위해서는 PK 와 FK 관계로 맺어져야 한다 (1:n 관계)

```
----JOIN 예시 TABLE----
===== ===== people ===== =====
id(PK) | name | job_id(FK)
1      | KIM  | 1
2      | LEE  | 1
3      | PARK | 2
4      | CHOI | 3

===== ===== job ===== =====
id(PK) | name 
1      | Sales
2      | Marketing
3      | Build
4      | Developer
```

#### INNER JOIN
    1. 두 테이블 연결시 가장 많이 사용 (일반적 조인의 뜻) 
    2. 두 테이블에서 공통된 값을 가지고 있는 필드들 레코드 반환[= 교집합]
    3. INNER JOIN을 JOIN이라고 써도 인식함
    4. ON 절은 JOin 

```SQL
SELECT <FIELDS_NAME>
FROM <1ST_TABLE_NAME>
    INNER JOIN <2ND_TABLE_NAME>
    ON <JOIN_조건>
WHERE <조건>;
    
e.g.
SELECT people.name, job.name
FROM people
    INNER JOIN job
    ON people.job_id, = job.id;

-- Result

```
#### OUTER JOIN
    1. 내부(INNER)와 다르게 한 쪽만 데이터 있어도 결과가 나옴

```SQL
SELECT <FIELDS_NAME>
FROM <1ST_TABLE_NAME>
    <LEFT or RIGHT or FULL> JOIN <2ND_TABLE_NAME>
    ON <JOIN_조건>
WHERE <조건>;
```

1. LEFT OUTER JOIN
    - LEFT의 모든 레코드와 RIGHT에서 LEFT와 공통된 필드 값을 가지고 있는 레코드들 반환
    - RIGHT에서 공통 값 가진 레코드가 없다면 NULL 반환
    ```SQL
    SELECT people.name, job.name
    FROM people
        LEFT JOIN job
        ON people.job_id = job.id;

    -- Result
    people.name === === job.name
    KIM            | Sales
    LEE            | Sales
    PARK           | Marketing
    CHOI           | Building
    ```

2. RIGHT OUTER JOIN
    - RIGHT의 모든 레코드와 LEFT에서 RIGHT와 공통된 필드 값을 가지고 있는 레코드를 반환
    - LEFT에서 공통된 값을 가진 레코드가 없다면 NULL 반환
    ```SQL
    SELECT people.name, job.name
    FROM people
        RIGHT JOIN job
            ON people.job_id = job.id

    -- Result
    people.name === === job.name
    KIM            | Sales
    LEE            | Sales
    PARK           | Marketing
    CHOI           | Building
    [NULL]         | Developer
    ```

3. FULL OUTER JOIN
    - 두 테이블에서 모든 값을 반환
    - 공통괸 값을 가지고 있지 않는 레코드가 있다면 NULL 반환
    - (이거 근데 MySQL에서 안된다는 말이 있음 UNION으로 하랍니다.)

4. 그 외
    1. A - B (A에 대한 B의 차집합)
        - A,B 가 겹쳐진 벤다이어그램에서 B 전체를 제외한 나머지 A 부분
        ```SQL
        SELECT <FIELDS_NAME>
        FROM <1ST(A)_TABLE_NAME>
            LEFT JOIN <2ND(B)_TABLE_NAME>
            ON A.key = B.key
        WHERE B.key IS NULL;
        ```

    2. B - A (B에 대한 A의 차집합)
        - A,B 가 겹쳐진 벤다이어그램에서 A 전체를 제외한 나머지 B 부분
        ```SQL
        SELECT <FIELDS_NAME>
        FROM <1ST(A)_TABLE_NAME>
            RIGHT JOIN <2ND(B)_TABLE_NAME>
            ON A.key = B.key
        WHERE A.key IS NULL;
        ```

    3. A ∪ B - A ∩ B (교집합 부분 빼고)
        - 근데 이거 FULL써야 하는거 같아서 나중에 UNION 알게 되면 그거로...

### CROSS JOIN
    1. 한쪽 테이블의 모든 레코드와 다른 테이블의 모든 레코드를 JOIN
    2. 두 테이블의 모든 레코드의 개수를 곱한 수 만큼 결과로 나옴
    
```SQL
SELECT <FIELDS_NAME>
FROM <1ST_TABLE_NAME> 
    CROSS JOIN <2ND_TABLE_NAME> ;
    WHERE <조건>;
```

```SQL
SELECT people.name, job.name
FROM job 
    CROSS JOIN people ;

-- Result

people.name === === job.name
KIM            | Sales
KIM            | Marketing
KIM            | Build
KIM            | Developer
LEE            | Sales
LEE            | Marketing
LEE            | Build
LEE            | Developer
PARK           | Sales
PARK           | Marketing
PARK           | Build
PARK           | Developer
CHOI           | Sales
CHOI           | Marketing
CHOI           | Build
CHOI           | Developer
```

### SELF JOIN
    1.  별도의 문법이 있는것이 아니고 자기 자신과 조인 하는 자체 조인이 된다.
    
```SQL
SELECT <FIELDS_NAME>
FROM <TABLE_NAME> <별칭1>
    (INNER) JOIN <TABLE_NAME> <별칭2>
    WHERE <조건>;
```

```SQL
SELECT * 
FROM people peo
	INNER JOIN people ple
	ON peo.id = ple.job_id  ;

-- Result
id === === name === === job_id === === id === === name === === job_id
1     | KIM        | 1            | 1        | KIM        | 1
1     | KIM        | 1            | 2        | LEE        | 1
2     | LEE        | 1            | 3        | PARK       | 2
3     | PARK       | 2            | 4        | CHOI       | 3
```

### UNION / UNION ALL
    1. JOIN 과는 별개로 두 테이블 합치기 (JOIN 과는 관계 없는 별개 동작)
    2. FULL OUTER JOIN 과 UNION/UNION ALL 과의 차이?
        - 일치하지 않는 레코드 포함 = FULL OUTER JOIN
        - 일치하지 않는 레코드 미포함 = UNION / UNION ALL

1. UNION
    - 두 테이블에서 중복 제거하고 합친 모든 레코드 반환

    ```SQL
    SELECT <TABLE1_FIELDS_NAME> FROM <TABLE1_NAME>
    UNION
    SELECT <TABLE2_FIELDS_NAME> FROM <TABLE2_NAME>;
    WHERE <조건>;
    ```

    ```SQL
    SELECT job.name FROM job 
    UNION
    SELECT people.name FROM people ;

    -- Result
    ======name=====
    Sales
    Marketing
    Build
    Developer
    KIM
    LEE
    PARK
    CHOI
    ```

2. UNION ALL
    - 두 테이블에서 중복 제거 않고 합친 모든 레코드 반환
    ```SQL
    SELECT <TABLE1_FIELDS_NAME> FROM <TABLE1_NAME>
    UNION ALL
    SELECT <TABLE2_FIELDS_NAME> FROM <TABLE2_NAME>;
    WHERE <조건>;
    ```

    ```SQL
    SELECT job.name FROM job 
    UNION ALL
    SELECT people.name FROM people ;

    -- Result
    ======name=====
    Sales
    Marketing
    Build
    Developer
    KIM
    LEE
    PARK
    CHOI
    ```