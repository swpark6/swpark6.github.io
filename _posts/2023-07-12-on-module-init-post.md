onModuleInit 에 대하여… 요청때마다 생성자가 필요한 자원(인스턴스)들은 초기화는 onModuleInit을 통하는게아닌, 직접 Construct에 넣어서 초기화 해주어야 함. @Injectable({scope: Scope:REQUEST}) 로 명시하겠습니다.
Nest의 관리밖에서 GC에 의해 수거되기 위함
참고로 @Logger() 를 의존하는 클래스는 요청 때마다 초기화되는 Correlation-id 때문에 Scope:REQUEST  로 동작합니다.

>WARNING
The lifecycle hooks listed above are not triggered for request-scoped classes. Request-scoped classes are not tied to the application lifecycle and their lifespan is unpredictable. They are exclusively created for each request and automatically garbage-collected after the response is sent.