---
tags:
  - type/note
aliases: 
lead: 
visual: 
created: 2025-01-07, 17:38
modified: 2025-01-07, 17:38
template-type: Frontmatter
template-version: "1.4"
icon:
---


# Java

<!-- Main STRUCTURE of my content -->


## LeetCode
### 876. Middle of the Linked List

```
 public class ListNode{
	int val;
	ListNode next;
	ListNode() {};
	ListNode(int val) {this.val = val;}
	ListNode(int val, ListNode next) {this.val = val; this.next = next;}
 }
 
 //1 - 2 - 3 - 4 - 5 - 6 >> Since the list has two middle nodes with value 3 and 4, we return the second one.
 // 1 - 2 - .... n >> int middleValue; >> if n^2 == 0 > middleValue = n/2; else middleValue = Math.ceil(n/2);
 // 
 class Solution{
	public ListNode middleNode(ListNode head){
		
	}
 }
```

<pre>

</pre>
```
// e.g ) ListNode nodeTest = ListNode(1, ListNode(2));

// e.g) ListNode nodeTest = ListNode(1, ListNode(2, ListNode(3) ));

//firstValue =  nodeTest.val, secondValue = nodeTest.next.val; , thirdValue = nodeText.next.next.val;

	List resultList = new ArrayList();
	resultList.add(head.val);
	ListNode nextNode = head.next;
	do{
		resultList.add(nextNode.val);
		nextNode = nextNode.next;
	}while(nextNode.next == null);
	
	int middleIdx = (resultList.size()%2 == 0)? (int)resultList.size()/2 : (int)Math.ceil(resultList.size()/2);
		
	if(resultList.size()%2 == 0) middleIdx = middleIdx +1;

	int idx = 1;// head.val이  idx =1
	ListNode agentNode = head.next;
		idx = 
	idx++;
	do{
		agentNode = agentNode.next ;
		idx++;
	}while(idx == middleIdx);
	
	return returnNode;
```

### Flux

> [!NOTE] Class Flux\<T\>
> 

	
- Flux.fromIterable

### Publisher/Subsriber Pattern

> [!NOTE]  The Publisher/Subscriber Pattern
>   이벤트가 핵심인 아키텍처를 구현
>   시스템 구성요소를 분리하는데 중요하게 쓰임
>   
>   이벤트 주도의 아키텍쳐 구현 및  시스템 구성요소를 분리하는데 핵심이 되는 디자인 패턴. 
> Publisher/Subscriber 패턴으로 알려진 커뮤니케이션 패러다임은 수신자가 모른 채 메시지를 공개하는 발신자를 포함한다. 메시지의 출처인 publisher를 모른 채 Subscriber는 1개 혹은 그 이상의 주제에 관심을 가지고 이에 대해 흥미로운 정보를 얻어낸다. 이 시스템의 유연성과 확장성은 이러한 publisher와 subscriber의 분리에 의해 더 향상된다. 
>   이 패턴은 특히 컴포넌트가 비동기적이고 독립적으로 통신할 필요가 있는 애플리케이션에 유용함

-  Key Concepts 
	- Publisher: 메시지를 보내는 Component
	- Subscriber: 메시지를 받는 Component
	- Message: 전송되는 데이터
	- Channel/Topic: 메시지가 보내지는 매개체
- 장점
	- Decoupling, Scalability, Flexibility, Asynchronous Communication
- 사용
```
interface Subscriber{ void update(String event, Object data) }

class PubSub{
    
}
```
 

### Subscriber

> [!NOTE] Interface Subscriber\<T\>
> 한 번 Subscriber의 객체를 Publisher.subscribe(Subscriber)의 형태로 건넸다면, onSubscribe(Subscription) 메서드가 호출된다. 이후엔 Subscription.request(long)이 호출될 때까지는 어떠한 알림도 못 받는다. 
- 요청을 보낸 후엔 
	- onNext(Object)가 1번 혹은 그 이상 호출된다. 최대 호출 횟수는 Subscription.request(long)에서 정의한 대로 수행된다. 
	- 보낼 이벤트가 더 이상 없을 경우엔 종료 상태임을 알리는 onError(Throwable) 혹은 onComplete() 둘 중 한 개가 호출된다. 
- Subscriber 인스턴스만 가능하다면 요청은 얼마든지 Subscription.request(long)을 통해 보낼 수 있다.


### Publisher

> [!NOTE] Interface Publisher\<T\>
> Publisher는 Subscriber(s)로 부터 받은 요청에 의해 일련의 연속된 요소를 가능한 무한히 제공하는 역할을 수행한다. 여러 개의 Subscriber가 다양한 시점에 동적으로 Publisher의 'subscribe'를 호출할 수 있다. 
- method 'subscribe'
	- Request [`Publisher`](https://www.reactive-streams.org/reactive-streams-1.0.3-javadoc/org/reactivestreams/Publisher.html "interface in org.reactivestreams") to start streaming data.
	- 몇 번이고 호출해도 되고, 호출 할 때마다 새로운 Subscription을 시작함. 각각의 Subscription은 오직 한 개의 Subscriber만을 위해 작동. 1개의 Subscriber는 반듸시 한 번에 한 개의 Publisher만 구독해야 함. 만약 Publisher가 구독시도를 거절하거나 그렇지 않고, 실패했다면, Subscriber.onError method를 통해 신호를 줄 것임

## JSONObject 

-  fromObject : 
```
public static JSONObject fromObject(Object object) {  
    return fromObject(object, new JsonConfig());  
}

JsonBeanProcessor processor = jsonConfig.findJsonBeanProcesor(bean.getClass());

private static JSONObject _fromString(String str, JsonConfig jsonConfig) {  
    if (str != null && !"null".equals(str)) {  
        return _fromJSONTokener(new JSONTokener(str), jsonConfig);  
    } else {  
        fireObjectStartEvent(jsonConfig);  
        fireObjectEndEvent(jsonConfig);  
        return new JSONObject(true);  
    }
}



```
- 설명
	- 1. param으로 받은 object가 어떤 클래스인지 유형별로 구분한다. 
	- 2. 아래 분류에 따라 해당 객체가 어떤 클래스의 객체인지에 따라 parse하는 method를 달리 호출
	- 3. 각 method에선 tokener로  나눠서 ch로 return
	- 4. ch를 StringBuffer에 붙여서 key, value의 형태로 JsonObject에 차례차례 쌓음
	- 5. JsonObject return
- Interface JsonBeanProcessor > processBean
	- parameter: bean, 현재 설정 환경
	-  return: input으로 들어온 빈을 나타내는 JSONObject를 리턴
- param인 Object 유형이 다음과 같은 케이스일 때
	- JSONObject 
	- DynaBean
	- JSONTokener
	- JSONString 
	- String
	- Map
	- Number도 아니고, Boolean도 아니고, String도 아니면
		- 배열일 때는 에러 표시
		- 그 외에는 

### JSONArray
- 설명
	- JSONArray jsonArray = new JSONArray();
	- Iterator elements = array.iterator();
	-  
![[Pasted image 20250213175830.png]]

### ResponseEntity\<T\>
-  HttpEntity 의 확장클래스이고, RestTemplate에서도 사용되고, @Controller 메서드에서도 사용된다.
- RestTemplate에서 사용할 때
```
ResponseEntity<String> entity = template.getForEntity("https://example.com", String.class);
String body = entity.getBody();
MediaType contentType = entity.getHeaders().getContentType();
HttpStatus statusCode = entity.getStatusCode();
```

- @Controller 메서드에서 리턴하는 값으로써, Spring MVC 패턴에서 사용될 때
```
@RequestMapping("/handle)
public ReponseEntity<String> handle(){
	URL location = ...;
	HttpHeaders responseHeader = new HttpHeaders();
	responseHeaders.setLocation(location);
	responseHeaders.set("MyResponseHeader", "MyValue");
	return new ResponseEntity<String>("Hello World", responseHeaders, HttpStatus.CREATED);

}
```
- ResponseEntity(T body, MultiValueMap<String, String> headers, HttpStatusCode statusCode)

### HttpHeaders
- Http 요청과 응답 헤더을 표시하는 데이터 구조로, 문자열로 된 헤더명과 여러 값이 있는 리스트 한 개를 매핑한다. 

### @RequestBody
- 설명: 이 어노테이션을 사용함으로써 request body를 읽을 수 있고, HttpMessageReader를 통해서 
객체로 풀어낼 수도 있다. SpringMVC과 달리 WebFlux에서는 이 어노테이션 선언이 reactive types 및 완전한 non-blocking reading을 지원하여 client-to-server 스트리밍을 가능하게 한다. 
	-  여기서의 'Body'는 Http 요청 본문을 의미한다. 따라서 JSON, XML, 혹은 기타 JAVA 객체가 아닌 다른 형태의 데이터를 받을 때는 무조건 @RequestBody로 받아야 한다. 
	- 그러면 @RequestParam 은 뭐냐! url 쿼리로 /somePath?strSeq=value로 즉 url parameter로 받을 때 사용합니다.
	- 그러면 @ResponseBody는 뭐냐! 말 그대로 리턴할 때 즉, 응답 목적으로 HttpBody를 리턴해줘야 할 때 사용합니다. 아래와 같이 사용합니다. 
```
public @ReponseBody ReponseEntity\<T\> blahblah(Object parma)){


}
```




---
## Questions

<!-- What remains for you to consider? --> 
- Streaming?
	-  Streaming Processing: 이 프로세스는 실시간 분석을 가능하게 하고, 데이터가 생성될 때 데이터가 전송될 수 있도록 작동한다. 
	-  Event Time vs Processing Time: 이벤트 타임은 해당 이벤트가 실제로 현실세계에서 발생하는 그 순간을 의미한다. 이벤트가 어떤 순서대로 발생했는지 에 대한 시나리오를 구성하는데 굉장히 중요하고, 이 지점은 데이터가 정확히 처리되어서 실제 발생 순서를 반영할 수 있게 만들어준다. 반면에 Processing time은 시스템이 이벤트 처리를 언제하는지에 대한 시점이고, 이건 실제 발생과 궤를 같이 하지는 않는다. 
	-  


## Terms
<!-- Links to definition pages -->
-  signal : to make a movement, sound, flash, etc that gives information or tells people what to do
	- e.g) signal sth to some : Flashing lights on a parked car usually signal a warning(to other drivers)
	- e.g)He was signalling (= giving a signal) with a [red](https://dictionary.cambridge.org/dictionary/english/red "red") [flag](https://dictionary.cambridge.org/dictionary/english/flag "flag").
	- e.g) signal for She signalled for [help](https://dictionary.cambridge.org/dictionary/english/help "help").
	- e.g)  [[ + that ]] She signalled to the [cars](https://dictionary.cambridge.org/dictionary/english/car "cars") behind her that they were going the [wrong](https://dictionary.cambridge.org/dictionary/english/wrong "wrong") way.
- publish: to print an article in a newspaper or magazine, or to make it avaliable online
- unbounded: very [great](https://dictionary.cambridge.org/dictionary/english/great "great"); [seeming](https://dictionary.cambridge.org/dictionary/english/seeming "seeming") to have no [limits](https://dictionary.cambridge.org/dictionary/english/limit "limits"):
- unbind(unbound) : <> bind
- serve(HELP ACHIEVE) : to hlep achieve sth or to be useful as sth
	- e.g) Nothing serves to explain the violent fighting we have seen recently
- emit: to send out a beamk noise, smell, or gas:
	- e.g) The machine emits a high-pitched sound when you press the button
- flatten: to become level and thinner or to cause sth oto become level and thinner
- stream: to send or receive sound or video directly over the internet as a continuous flow: on Youtuve, millions of videos are streamed every day. 
- siginify: to be a sign of sth, to mean
	- e.g) Nobody really knows what the marks on the ancient stones signify
	- e.g) The number 30 on a road sign signifies that the speed limit is 30 miles an hour.
- time window: a fixed interval of time when the data stream is processed fo rquery and mining process
- mining process: 업무 프로세스 데이터를 분석하여 개선점을 찾는 기법(로그 수짐, 프로세스 모델 생성, 성능 분석 및 개선)

## References
<!-- Links to pages not referenced in the content -->
- https://dictionary.cambridge.org/help/codes.html


