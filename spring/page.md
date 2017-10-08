Page
============

Paginiation을 간편히 구현할 수 있다.

## 주의점

restTemplate 으로 응답을 받을 때, 응답이 Jackson converter를 통해 바로 변환이 되지 않는다.
이유는 *Page*는 interface이고 *PageImpl*은 no-args constructor가 없기 때문이다.
따라서 다음과 같이 *CustomPageImpl*을 만들어준다

     class CustomPageImpl<T> extends PageImpl<T> {
         CustomPageImpl() {
             super(new ArrayList<T>());
         }
     }
     
다음과 같이 요청하면 잘 변환되서 온다

    restTemplate.exchange(url, GET, null, new ParameterizedTypeReference<CustomPageImpl<Permission>>() {})


## 참고

<https://stackoverflow.com/questions/34099559/how-to-consume-pageentity-response-using-spring-resttemplate>
<https://blog.thecookinkitchen.com/how-to-consume-page-response-from-a-service-in-spring-boot-97293c18ba>

