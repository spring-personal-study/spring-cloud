## spring-cloud
스프링 클라우드 실습 프로젝트

프로젝트 내에 없는 정보(카프카 설정정보 등)는 
- https://reminiscent-headlight-ee3.notion.site/6d240164d4ec4ee29762d759d6d1a7c8?v=6414875cb9b44edba02325a2f8b498b5

링크에 정리되어 있습니다.


### 게이트웨이서버
- api-gateway-service
  - https://github.com/spring-personal-study/spring-cloud-gateway


### 공통환경설정서버
- msa-config-service
  - https://github.com/spring-personal-study/spring-cloud-config-service


### 공통 프로파일 및 설정 정보
- https://github.com/spring-personal-study/spring-cloud-config-yml


### 서비스 디스커버리(eureka)에 등록될 애플리케이션(cloud-client) 목록
- msa-user-service
  - https://github.com/spring-personal-study/spring-cloud-user-service
- msa-catalog-service
  - https://github.com/spring-personal-study/spring-cloud-catalog-service
- msa-order-service
  - https://github.com/spring-personal-study/spring-cloud-order-service


--- 

## 전체 어플리케이션 개요

![image](https://user-images.githubusercontent.com/37533326/161421789-a7657d88-6ff6-4afc-a902-c46c146348af.png)



## 전체 어플리케이션 구성

![image](https://user-images.githubusercontent.com/37533326/161421623-9cedb1be-6c99-46d1-8f39-3d7f79a0ecf7.png)


## 각 어플리케이션 구성 요소

- Eureka Server (ecommerce)
  - 마이크로서비스 등록 및 검색

- API Gateway Server (api-gateway-service)
  - 마이크로서비스 부하 분산 및 서비스 라우팅

- Config Server (msa-config-service)
  - 공통 프로파일 정보 및 설정 정보

- Microservice List
  - 회원, 주문, 상품(카탈로그) 

- Queuing System (카프카)
  - 마이크로서비스 간 메시지 발행 및 구독

## 기능 구현

### Gateway
- Spring Security를 활용한 JWT 인증 필터 (Gateway) 
- 유저, 주문, 상품 서비스 라우팅

### Config
- 설정정보 읽기 및 각 마이크로서비스에 설정정보 전달

### API
- USER
  - 회원 등록, 전체 조회, 단건 조회, (인증 필터구현을 통한)로그인, 서버 헬스체크
- ORDERS
  - 주문 등록, 특정 회원의 모든 주문내역 조회, 서버 헬스체크
- CATALOG
  - 카탈로그 조회, 서버 헬스체크
