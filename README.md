# JPA가 실무에서 어려운 이유
1. 객체와 테이블을 잘 설계하고 매핑하는게 중요하다.
2. 실무에서는 테이블이 많기 때문에 이를 적용하기 어렵다.
3. 실제로 적용했다가 매핑을 잘못하는 경우가 있다.

# 객체와 테이블을 제대로 설계하고 매핑하는 방법

# JPA 내부 동작 방식 이해
1. JPA가 어떤 SQL을 만들어 내는가?
2. JPA가 언제 SQL을 실행하는가?
    * EntityManager->flush() 호출
    * EntityManager->commit() 호출 (flush 자동 호출)
    * JPQL 쿼리 실행 (flush 자동 호출)

# 객체를 중심으로 생각해보자

# 패러다임 불일치 해결

# 자유로운 객체 그래프 탐색
1. 동일한 트랜잭션에서 조회한 엔티티는 같음을 보장

# Persistence Context 이점
1. 1차 캐시
    * Entity Manager 내부에서 관리
    * EntityManager -> find 수행 시 1차 캐시에서 우선적으로 조회
        > 만약 캐시에 원하는 데이터가 없을 경우 DB 조회 후 캐시에 저장하고 이를 반환 
2. 동일성(identity) 보장
3. 트랜잭션을 지원하는 쓰기 지연(transactional write-behind)
4. 변경 감지(Dirty Checking)
5. 지연 로딩(Lazy Loading)

# Persistence Context 관련 Method
* EntityManager->clear() : 영속성 컨텍스트 초기화