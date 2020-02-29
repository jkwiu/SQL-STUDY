# SQL-STUDY
This is for SQL Study.<br/>
This is for beginer for sql.<br/>
I'll follow my sql book step by step.
------------------------------------------
1. 데이터베이스와 SQL
   1. DB(Database)
      1. DBMS(Database Management System)
         1. DBMS가 필요한 이유
            1. 생산성
               1. 기본기능이 구현되어 있어 효율적
            2. 기능성
            3. 신뢰성
         2. SQL
            1. DBMS와 대화를 하기 위해 필요한 것
            2. 요점
               1. 관계형 데이터베이스에서 사용한다
               2. SQL 명령의 종류
                  1. DML(Data Manipulation Language)
                     1. 데이터 조작
                  2. DDL(Data Definition Language)
                     1. 데이터 정의
                  3. DCL(Data Control Language)
                     1. 데이터베이스 제어
         3. 종류
            1. RDBMS(Relational Database Management System)
   2. 다양한 데이터베이스
      1. 종류
         1. 계층형 데이터베이스
            1. 폴더와 파일 등의 계층구조로 데이터를 저장하는 방식
         2. 관계형 데이터베이스
         3. 객체지향 데이터베이스
            1. 객체 그대로를 데이터베이스의 데이터로 저장하는 것
         4. XML 데이터베이스
            1. XQuery라는 전용 명령어를 사용한다.
         5. 키-밸류 스토어(KVS)
            1. NoSQL이라는 슬로건에서 파생된 데이터베이스
            2. 키-밸류 조합으로 데이터를 저장
      2. RDBMS제품 종류
         1. Oracle, DB2, SQL Server, PostgreSQL, MySQL, SQLite
         2. **SQL에는 프로그램마다 방언이 있다. 방언대신에 ISO나 ANSI가 결정한 표준 SQL을 사용하는 편이 좋다.**
   3. 데이터베이스 서버
      1. 실제로 데이터베이스에 접속하는 것은 PHP, Ruby, ASP.NET, JAVA와 Servlet과 같은 CGI(동적 컨텐츠를 위한 확장 방식) 
2. 테이블에서 데이터 검색
   1. DESC [table명]
      1. 테이블 참조
   2. 자료형
      1. INTEGER형
      2. CHAR형
         1. 고정 길이 문자열 자료형
      3. VARCHAR형
         1. 가변 길이 문자열 자료형
      4. DATE형
      5. TIME형
   3. 검색 조건 지정하기
      1. SELECT 열1, 열2.... FROM 테이블명 // 열지정
      2. WHERE조건 // 행 지정
         1. SELECT a, b, c FROM sample WHERE a=1;
            1. a,b,c열에서 행이 a=1인 것을 조회하는 것을 의미
   4. 패턴 매칭에 의한 검색
      1. 열 LIKE 패턴
         1. ``%``는 와일드카드라고 불리는 메타문자
            1. 전방일치
               1. ``문자열%``
            2. 중간일치
               1. ``%문자열%``
            3. 후방일치
               1. ``%문자열``
            4. **%**을 포함하는 데이터를 검색하고 싶을 때
               1. ``이스케이프``를 이용
                  1. WHERE text LIKE '%\%%'
         2. ``'``를 기술하고 싶으면, ``''``를 써준다.
3. 정렬과 연산
   1. 정렬(ORDER BY)
      1. SELECT 열명 FROM 테이블명 WHERE 조건식 ORDER BY 열명
      2. 내림차순으로 정렬
         1. SELECT 열명 FROM 테이블명 WHERE 조건식 ORDER BY 열명 DESC
      3. 오름차순으로 정렬
         1. SELECT 열명 FROM 테이블명 WHERE 조건식 ORDER BY 열명 ASC
      4. 복수 열로 정렬 지정
         1. SELECT 열명 FROM 테이블명 WHERE 조건식 ORDER BY 열명1, 열명2
      5. 결과 행 제한하기
         1. SELECT 열명 FROM 테이블명 LIMIT 행수 [OFFSET 시작행]
      6. 데이터베이스 서버 내부에서 WHERE구 -> SELECT구 순서로 처리 된다.
         1. **SELECT구에서 지정한 별명은 WHERE구 안에서 사용할 수 없다**
      7. ORDER BY는 서버 내부에서 가장 마지막으로 처리되므로 SELECT에서 지정한 별명을 사용할 수 있다.
      8. **WHERE구 -> SELECT구 -> ORDER BY 구**
      9. NULL로 연산하면 결과는 NULL이 된다.
      10. 함수
          1.  MOD()
          2.  ROUND(): 반올림
          3.  CONCAT함수를 이용해 두 데이터의 열의 행 값을 합칠 수 있다.
          4.  SUBSTRING()
          5.  TRIM()
          6.  CHARACTER_LENGTH()
      11. 날짜 연산
          1.  CURRENT_TIMESTAMP()
          2.  TO_DATE('2020/03/01', 'YYYY/MM/DD')
          3.  DATEDIFF(): 두 날짜의 차이
      12. CASE문으로 데이터 변환
          1. CASE WHEN 조건식1 THEN 식1
           1.  [WHEN 조건식 2 THEN 식2 ...]
              2.  [ELSE 식3]
          2.  END
          3. 어디에서나 사용할 수 있다.(WHERE, SELECT, ORDER BY) 
          4. ELSE를 생략할 경우 NULL이 된다.
4. 데이터의 추가, 삭제, 갱신
   1. 행 추가
      1. INSERT INTO 테이블명 VALUES(값1, 값2, ...)
   2. 삭제하기
   3. 데이터 갱신하기
   4. 물리삭제와 논리삭제
      1. 물리삭제
         1. DELETE명령어를 사용해 직접 데이터를 삭제
      2. 논리삭제
         1. 테이블에서 실제로 행을 삭제하는 대신, UPDATE를 이용해 ``삭제플레그`` 값을 유효하게 갱신해두자는 발상에 의한 삭제방법
5. 집계와 서브쿼리
   1. 행 갯수 구하기
      1. SELECT COUNT(*) FROM 테이블명
      2. 집계함수는 집합 안에 NULL값이 있을 경우 무시한다.
   2. DISTINCT로 중복제거 <-> ALL
   3. GROUP BY
      1. 내부처리 순서
         1. WHERE구 -> GROUP BY 구 -> SELECT 구 -> ORDER BY 구
   4. 서브쿼리
      1. (SELECT 명령)
      2. SELECT구에서 단일 열을 리턴받고 싶으면 단일 열을 지정해준다.
6. 데이터베이스 객체의 작성과 삭제
   1. SELECT, INSERT, DELETE, UPDATE는 DML, 그리고 이것은 DDL
   2. CREATE로 작성(CREATE TABLE)
      1. TABLE을 작성
         1. CREATE TABLE
      2. VIEW를 작성
         1. CREATE VIEW
   3. DROP으로 삭제(DROP TABLE)
      1. TRUNCATE TABLE 테이블명(모든 행을 삭제)
   4. ALTER로 변경
      1. ALTER TABLE 테이블명 변경명령
      2. 열 추가
         1. ALTER TABLE 테이블명 ADD 열 정의
      3. 열 속성 변경
         1. ALTER TABLE 테이블명 MODIFY 열 정의
      4. 열 이름 변경
         1. ALTER TABLE 테이블명 CHANGE [기존 열 이름][신규 열 정의]
      5. 열 삭제
         1. ALTER TABLE 테이블명 DROP 열명
   5. 제약
      1. 자식 테이블 측에서는 외부키(FOREIGN KEY)를 지정해 부모 테이블을 참조한다. 부모 테이블에서 참조될 열은 반드시 유일성(UNIQUE KEY, PRIMARY KEY)을 가진다.
      2. 열 제약
         1. 한 열에 제약
      3. 테이블 제약
         1. 복수의 열에 제약
      4. 제약 추가
         1. 테이블 제약 추가
            1. ALTER TABLE 테이블명 ADD CONSTRAINT pkey_sample631 PRIMARY KEY(a)
         2. 제약삭제
            1. ALTER TABLE sample631 MODIFY c VARCHAR(30)
   6. 이진트리 검색
7. 복수의 테이블 다루기
   1. UNION으로 합집합 구하기
      1. ORDER BY로 지정할 때는 마지막 SELECT명령에만 지정한다.
         1. SELECT a as c FROM sample71_a 
         2. UNION 
         3. SELECT b as c FROM sample71_b ORDER BY c;
   2. 테이블 결합(곰집합)
      1. FROM구에 복수의 테이블을 지정하면 교차결합을 한다.
      2. 결합은 열 방향으로 확대된다.
      3. 내부결합
         1. 교차결합일 경우 WHERE절에 조건을 걸어주면 깔끔한 결과가 나옴
         2. INNER JOIN으로 내부결합하기
            1. 두 개의 테이블을 가로로 결합할 수 있다.
            2. 외부키
               1. 다른 테이블의 기본키를 참조하는 열이 외부키가 된다.
            3. 자기결합(Self Join)
               1. 별명을 붙일 수 있는 기능을 이용해 같은 테이블끼리 결합하는 것
      4. 외부결합(어느 쪽을 기준으로 결합할 것이냐)
         1. LEFT JOIN
         2. RIGHT JOIN 
8. 데이터베이스 설계
   1. 논리명
      1. ``상품명``
   2. 물리명
      1. ``PRODUCT_NAME``
   3. 기본키
      1. 테이블을 작성할 때 기본키 제약을 거는 경우 주의해야한다.
   4. 정규화
      1. 데이터를 규정된 올바른 형태로 개선하는 것
         1. 제1 정규형
            1. 반복되는 데이터를 열방향이 아닌 행방향으로 늘리는 것
         2. 제2 정규형
            1. 기본키에 중복이 없는지 조사
         3. 제3 정규형
            1. 기본키 이외의 부분에서 중복이 없는지 조사
      2. 정규화의 목적
         1. ``하나의 데이터는 한 곳에 있어야한다.``