# RESTful API

---

## 면접 질문 예시

> "RESTful API에 대해 설명하고, GraphQL과 gRPC와 비교해주세요."

---

<details>
  <summary><h2> 평가 요소 및 평가 요소 별 모범 답안</h2></summary>

  ### 1. RESTful(Representational State Transfer) API => 단순함
  - 포함내용
    - 정의: 웹 기반 애플리케이션에서 클라이언트와 서버 간의 통신을 위한 아키텍처 스타일
    - 특징: 리소스를 URI로 표현하고, HTTP메서드(GET, POST, PUT, DELETE)를 사용해 작업을 수행 / 무상태성
    - 장/단점: 단순하고 직관적이며 데이터 형식에 유연하지만, 복잡한 관계형 데이터 조회나 다수의 자원에 대한 동시 요청에는 한계가 있다.
    - 예시 코드
        <details>
      
        ``` http
         GET /users/1
        ```
        
        ``` java
        @RestController
        @RequestMapping("/users")
        public class UserController {
        
            @GetMapping("/{id}")
            public User getUser(@PathVariable Long id) {
                return new User(id, "Alice", "alice@example.com");
            }
        }
        
        class User {
            private Long id;
            private String name;
            private String email;
        
            // 생성자, Getter, Setter 생략
        }
        ```
        </details>

  - <details>
    <summary> RESTful API 답안 예시 : </summary>
    
      > "RESTful API는 웹 기반 애플리케이션에서 클라이언트와 서버 간의 통신을 위한 아키텍처 스타일로, 리소스를 URI로 표현하고 HTTP 메서드를 사용해 작업을 수행한다. 단순하고 직관적이며 데이터 형식에 유연하지만, 복잡한 관계형 데이터 조회나 다수의 자원에 대한 동시 요청에는 한계가 있다."
    </details>

  - <details>
    <summary>비교 답안 예시 : </summary>
    
      > "RESTful API는 리소스를 URI로 표현하고 HTTP 메서드를 이용해 요청을 처리하는 단순하고 직관적인 아키텍처 스타일이며,
GraphQL은 클라이언트가 필요한 데이터만 선택적으로 요청할 수 있는 유연하고 효율적인 쿼리 기반 API이고,
gRPC는 HTTP/2와 Protocol Buffers를 기반으로 한 고성능 바이너리 통신 방식으로, 서버 간 통신에 적합한 RPC 프레임워크입니다. REST는 단순성과 직관성을, GraphQL은 데이터 요청의 유연성을, gRPC는 고성능과 서버 간 통신 효율성을 강점으로 가진 API 방식입니다."
    </details>
</br>
</br>
</br>


  ### 2. GraphQL API => 유연성
  - 포함내용
    - 정의: 사용자가 정의한 스키마 기반 데이터 타입 시스템을 이용해 쿼리를 실행하는 서버 측 런타임
    - 특징: 클라이언트가 필요한 데이터만 선택하여 요청할 수 있어, 네트워크 트래픽을 줄이고 프론트엔드 개발에 유리 / 단일 엔드포인트에서 다양한 요청 처리 가능
    - 장/단점: 유연하고 효율적인 데이터 검색이 가능하지만, 스키마 정의, 리졸버 관리 등으로 인해 서버 구현이 복잡하고, 클라이언트가 작성한 과도하게 복잡한 쿼리는 성능 저하를 초래할 수 있다.
    - 예시 코드
        <details>
          
        ``` graphql
        query {
            user(id: 1) {
                name
                email
            }
        }
        ```
        
        ``` java
        @Component
        public class UserQueryResolver implements GraphQLQueryResolver {
        
            public User getUser(Long id) {
                return new User(id, "Alice", "alice@example.com");
            }
        }
        
        
        type Query {
            user(id: ID!): User
        }
        
        type User {
            id: ID!
            name: String
            email: String
        }
        ```
        </details>

</br>
</br>
</br>

  ### 3. gRPC => 고성능
  - 포함내용
    - 정의: Google에서 개발한 고성능 RPC(Remote Procedure Call) 프레임워크 / HTTP/2 기반 전송 및 Protocol Buffers(Protobuf)를 인터페이스 정의 언어(IDL) 및 직렬화 형식으로 사용
    - 특징: 낮은 지연 시간과 높은 처리량을 제공하며, 서버 간 통신에 특히 적합 / 브라우저에서 직접적으로 HTTP/2 및 Protobuf를 다루기 어렵기 때문에 일반적으로 REST 또는 gRPC-Web으로 우회
    - 예시 코드
        <details>
          
        ``` java
        ManagedChannel channel = ManagedChannelBuilder.forAddress("localhost", 50051)
                .usePlaintext()
                .build();
        
        UserServiceGrpc.UserServiceBlockingStub stub = UserServiceGrpc.newBlockingStub(channel);
        
        UserRequest request = UserRequest.newBuilder().setId(1).build();
        UserResponse response = stub.getUser(request);
        
        System.out.println(response.getName() + " / " + response.getEmail());
        ```
        ``` java
        public class UserServiceImpl extends UserServiceGrpc.UserServiceImplBase {
            @Override
            public void getUser(UserRequest request, StreamObserver<UserResponse> responseObserver) {
                UserResponse response = UserResponse.newBuilder()
                        .setName("Alice")
                        .setEmail("alice@example.com")
                        .build();
                responseObserver.onNext(response);
                responseObserver.onCompleted();
            }
        }
        
        syntax = "proto3";
        
        option java_package = "com.example.grpc";
        option java_outer_classname = "UserProto";
        
        service UserService {
          rpc GetUser(UserRequest) returns (UserResponse);
        }
        
        message UserRequest {
          int64 id = 1;
        }
        
        message UserResponse {
          string name = 1;
          string email = 2;
        }
        ```
        </details>

</br>
</br>
</br>



</details>
