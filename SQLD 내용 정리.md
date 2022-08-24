#### SQL 시험용 정리

## 목차

1. 관계형 데이터베이스 개요
2. SELECT 문
3. 함수
4. WHERE 절
5. GROUP BY, HAVING 절
6. ORDER BY 절
7. JOIN
8. STANDARD JOIN
*********************************************

1. 관계형 데이터베이스 개요
  * 데이터 모델에서 엔터티, 인스턴스, 속성은 테이블, 로우, 컬럼에 대응된다.

***************************************

2. SELECT 문
  * 기본형 SELECT 컬럼명 FROM 테이블명 ;
  * TABLE명 ALIAS 표기 시 반드시 ALIAS 사용

    <PRE><CODE> SELECT TAB.COL FROM TAB T WHERE T.COL ='A'; < 오류 발생 </CODE></PRE>
  
  * NULL을 포함한 가로연산의 결과는 __NULL__ 이다.
  
3. 함수
  * 문자열 함수 
    - CHR(숫자인수) 
      + 숫자인수에 맞는 ASCII 문자 출력 EX) SELECT CHR(65) FROM DUAL; > A
    - LOWER(문자열)
      + 소문자로 변환
    - UPPER(문자열)
      + 대문자로 변환
    - LTRIM(문자열[,특정문자])
      + 옵션이 없을 시 문자열 왼쪽의 공백 삭제
      + 옵션이 있다면 문자열의 왼쪽에서부터 특정문자를 __하나씩__ 비교하여 같으면 삭제
     <PRE><CODE> SELECT LTRIM('SQLD','DLS') FROM DUAL; > NULL </CODE></PRE>  
    - RTRIM(문자열[,특정문자])
      + 옵션이 없을 시 문자열 오른쪽의 공백 삭제
      + 옵션이 있다면 문자열의 오른쪽에서부터 특정문자를 __하나씩__ 비교하여 같으면 삭제
     <PRE><CODE> SELECT RTRIM('SQLD','DLS') FROM DUAL; > 'SQ' </CODE></PRE>  
    - TRIM([위치][특정문자][FROM]문자열)
      + 옵션이 없을 시 문자열 왼쪽,오른쪽의 공백 삭제
      + 옵션이 있다면 위치 값 방향으로 문자열에서 부터 특정문자를 __하나씩__ 비교하여 같으면 삭제
      + 위치 옵션 : LEADING(왼쪽), TRAILING(오른쪽), BOTH(양쪽)
      + __단, 특정문자는 한개의 캐릭터만 가질 수 있음__(검증필요)
     <PRE><CODE> SELECT TRIM(LEADING 'SQD' FROM 'SQLDFASCD') FROM DUAL; > '오류' </CODE></PRE>
    - SUBSTR(문자열,시작점,길이)
      + 엑셀의 MID와 유사함
    - LENGTH(문자열)
    - REPLACE(문자열, 변경전 문자열[,변경후 문자열])
      + 옵션이 없을 시 변경전 문자열을 삭제함   
  
   * 숫자 함수
    - ABS(수) > 절대값
    - SIGN(수) > 부호 (양 : +1, 0 : 0 , 음 : -1)
    - ROUND(수[,자릿수]) > 자릿수 까지 반올림 일의 자릿수는 0으로 표기 십의 자릿수는 -1임;
    - TRUNC(수[,자릿수]) > 자릿수 까지 버림 일의 자릿수는 0으로 표기 십의 자릿수는 -1임;
    - CEIL(수) > 소수점 이하의 수 올림
    - FLOOR(수) > 소수점 이하의 수 내림
    - MOD(수1,수2) > 수1/수2의 __나머지__를 구함; __음수/음수__는 음수 나머지로 계산됨   
  
   * 날짜 함수
    - SYSDATE > 현재 데이터
    - EXTRACT(특정단위 FROM 날짜 데이터)
      + 날짜 데이터에서 특정단위값만 추출함
      + 특정단위(YEAR,MONTH,DAT,HOUR,MINUTE,SECOND)
    - ADD_MONTHS(날짜데이터, 특정개월수)
      + 날짜데이터 + __개월__ , 단, 2월처럼 계산했는데 없는 날짜면 그달의 마지막 날이 출력됨
  
   * 변환 함수
    - TO_NUMBER(문자열) > 문자열을 숫자로
    - TO_CHAR(수 OR 날짜[,포맷]) > 수 또는 날짜를 포맷형식의 문자로 변환    
    - TO_DATE(문자열,포맷) > 문자를 날짜로
  
   * NULL 관련 함수
    - NVL(인수1,인수2) > 인수1을 출력하되 NULL일때는 인수2 출력
    - NULLIF(인수1,인수2) > 인수1 과 인수2 같으면 NULL, 아니면 인수1 출력
    - COALESCE(인수1, 인수2, 인수3)
      + 가로로 된 인수들 중에서 왼쪽부터 살펴보아 최초의 NULL이 아닌 값을 출력
      + 사용 예시 : 어떤 INSTANCE의 NULL이 아닌 연락처 찾기
  
    * CASE 문
     - CASE 컬럼명 WHEN 조건 TEHN 결과 WHEN 조건 TEHN 결과 .... ELSE 모든 조건 통과시 결과 값 END
     - CASE WHEN 컬렴명 포함 조건 TEHN 결과 WHEN 컬럼명 포함 조건 TEHN 결과 ELSE .. END
     - DECODE(컬럼명, 조건1, 결과1.;......, ELSE값)
  
              
  4. WHERE 절
    * 부정 비교 연산자
      > 같지 않음 (!=, ^=, <>)
    * SQL 연산자
      - WHERE 컬럼 BETWEEN A AND B
      - WHERE 컬럼 LIKE 비교 문자열
      - WHERE 컬럼 IS (LIST1,LIST2...)
      - WHERE 컬럼 IS NULL(O)
  
   __COMMIT POINT(20220824)__
  
  
  
  
  
