Idempotent
====
[HTTP 1.1 - Method Definitions]을 보면, Idempotent 에 대한 설명이 나온다.
기본적으로 HTTP의 모든 method들은 Idempotent하다. 모든 요청은 side-effect가 없고, 항상 같은 결과를 내기 때문이다.
이를 어떻게 생각해야 하나면, 
예를들어 DELETE 명령을 날리는 경우, 서버에 해당 정보가 삭제되었을 것이라 생각할 수 있다.
한번을 보내나 여러번 보내나 삭제되었다는 결과는 같다.
POST로 생성하거나 PUT으로 수정하는 경우도 마찬가지다. 한번 실행하나 여러번 실행하나 서버에 저장된 결과는 동일하다.

즉 모든 METHOD는 기본적으로 Idempotent한데, method의 sequence는 Idempotent할 수도 있고, 아닐수도 있다.
예를들어 나중에 요청이 앞의 요청에 의존하는 경우가 그렇다. 
Idempotent하려면, sequence중 일부 또는 전체를 재실행 해도 결과가 변하지 않아야 한다.
예를들어 POST, PUT, DELETE 하는 경우, 이중에 일부를 재실행 하면 서버의 저장값이 달라진다
GET, OPTIONS, HEAD, HEAD 하는 경우, 일부를 재실행 해도 서버의 데이터는 동일하고, response도 같다. 

## 참고
[HTTP 1.1 - Method Definitions]: https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html "HTTP SPEC"