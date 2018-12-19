# Istio 기초 다지기 2- Circuit Breaker 편

이번 실습에서는 Istio 상에서 Circuit Breaker를 배포해봅니다.
본 튜토리얼은 Istio의 실습 예제 **[istio-circuitbreaker](https://istio.io/docs/tasks/traffic-management/circuit-breaking/)** 를 참고합니다.


## 1. 배포할 환경
* httpbin: CircuitBreaker 정책을 적용할 대상 애플리케이션으로, 이미 Envoy를 주입하여 배포 완료된 상태
* fortio-client: httpbin 서비스로 트래픽을 전송하기 위한 클라이언트이며, 로드 테스팅 하는 툴 
