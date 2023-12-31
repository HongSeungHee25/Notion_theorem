# ROWNUM
: Oracle의 ROWNUM은 결과 집합의 각 행에 대해 할당되는 가상의 컬럼입니다. ROWNUM은 행의 순서를 나타내며, 결과 집합에 대한 순서를 제어하거나 특정 행을 선택하기 위해 사용됩니다.

# ROWNUM 특징
+ ROWNUM은 1부터 시작하여 결과 집합의 각 행에 할당됩니다.
+ SELECT 문의 WHERE 절이나 ORDER BY 절에서 ROWNUM을 사용하여 행을 필터링하거나 정렬할 수 있습니다.
+ ROWNUM은 쿼리 결과를 가져온 이후에 할당되므로, ROWNUM 값을 사용하여 쿼리 결과 집합을 변경할 수 없습니다.
+ ROWNUM은 결과 집합의 행 번호를 나타내므로, 정렬이나 필터링된 결과에 따라 ROWNUM 값이 변경될 수 있습니다.
+ ROWNUM은 등호(=)를 사용하여 비교할 수 없으며, 부등호(<, >, <=, >=)를 사용하여 비교할 수 있습니다.

## ROWNUM 예시 코드
    SELECT *
    FROM employees
    WHERE ROWNUM <= 10;
    ┗> 위의 예시에서는 employees 테이블에서 처음 10개의 행만 선택합니다. ROWNUM이 1부터 시작하므로 ROWNUM <= 10을 조건으로 사용하여 10개의 행을 선택할 수 있습니다.

*ROWNUM은 Oracle에서 자주 사용되는 기능 중 하나이며, 행을 제한하거나 정렬된 결과를 얻기 위해 유용하게 활용됩니다. 다만, ROWNUM을 사용할 때 주의해야 할 점은 정렬된 결과에서 ROWNUM을 사용하면 예상과 다른 결과를 얻을 수 있으므로 쿼리를 신중하게 작성해야 합니다.*

## ROWNUM 기본적인 형식
    - ROWNUM은 쿼리 결과 집합에서 각 행에 할당되는 유일한 순번입니다. ROWNUM은 일반적으로 행 번호를 나타내며, 1부터 시작하여 결과 집합의 첫 번째 행부터 차례대로 증가합니다.

    SELECT *
    FROM 테이블명
    WHERE ROWNUM <= n;
    ┗> 위의 코드는 특정 테이블에서 ROWNUM 이 n 이하인 행들을 반환합니다. ROWNUM은 필터 조건으로 사용되며, 결과 집합에 반환되는 행의 수를 제한하기 위해 사용될 수 있습니다.