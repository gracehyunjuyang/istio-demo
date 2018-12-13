# Istio 기초 다지기

## Istio sidecar 주입
배포되는 애플리케이션 컨테이너를 istio service mesh 에서 관리하도록 하기 위해서는 sidecar를 주입해야 하는데,
sidecar는 아래 두가지 방법으로 배포가 가능합니다.

* 수동 주입 - 애플리케이션 컨테이너 배포시 sidecar를 함께 배포
* 자동 주입 - 특정 namespace 에 애플리케이션 컨테이너 배포시 별도의 명령어 없이 sidecar가 자동 주입 되도록 label 설정

이 중에서 이번 튜토리얼에서는 **auto injection** 을 설정해 봅니다.

1. **default** namespace 정보 확인
~~~
kubectl describe namespace default
~~~

2. **default** namespace에 `istio-injection=enabled` 값 설정
~~~
kubectl label namespace default istio-injection=enabled
~~~

3. label이 반영된 namespace 정보 확인
~~~
kubectl describe namespace default
~~~

![istio auto injection](./images/istio-basic-1.png)

4. 이제 간단하게 예제 애플리케이션을 배포 가능
~~~
kubectl apply -f [bookinfo.yaml](./bookinfo/bookinfo.yaml)
~~~
![istio deploy bookinfo](./images/istio-basic-2.png)

5. 배포된 애플리케이션과 서비스 확인
~~~
kubectl get pods
kubectl get services
~~~
![istio deploy bookinfo](./images/istio-basic-3.png)
![istio deploy bookinfo](./images/istio-basic-4.png)




* 자동으로 sidecar 주입하도록 **namespace** 설정
애플리케이션


Circuit Breaker
