---
tags:
  - type/note
aliases: 
lead: Lead paragraph goes here
visual: "![[image.jpg]]"
created: 2025-02-06, 15:24
modified: 2025-02-06, 15:24
template-type: Note
template-version: "1.7"
---
# Javascript


> [!Note]
> `= this.lead`

---
## function

- event.preventDefault()
```
  어떤 이벤트를 명시적으로 처리하지 않은 경우 해당 이벤트에 대한 사용자 에이전트의 기본동작을 실행하지 않도록 지정
```

- event.stopPropagation()
```
 Event 인터페이스가 현재 이벤트가 capturing과 bubling 전파가 일어나지 않도록 방지한다. 
```
	
	
## Terms
-  signature
	- method의 input과 output 정의 

- Interface
		자바스크립트에는 보통 자바나 C# 자체에서 정의하는 인터페이스 같은 개념은 없다.  다만 비슷한 개념을 구사할 수는 있다. 객체와 클래스를 사용하여, 본인 스스로의 인터페이스를 정의하고 구현하면 된다. 
		Q. 그렇다면 인터페이스는 어떻게 정의하는가? 
			- A. 자바스크립트에서 인터페이스는 한 클래스가 반드시 수행해야하는 method signatures의 세트라고 볼 수 있다. 

- EventTarget
		EventTarget 인터페이스는 이벤트를 받을 수 있는 객체에 의해 수행되며, 이벤트의 모든 타겟은 이 인터페이스와 관련된 세 개의 메서드를 구현한다.

-  Event
		한 개의 이벤트는 사용자 행위에 의해 발동되거나 비동기 업무의 처리를 대표하는 API에 의해 생성되기도 한다. HTMLElement.click()를 호출함으로써 프로그램적으로 발동될 수 도 있다. 
-  Event Listener
		이벤트 리스너는 기본적으로 하나의 이벤트가 발생하기를 기다리는 한 개의 기능이라고 할 수 있다. 이 이벤트는 마우스 클릭일 수도 있고, 폼을 제출하는 것일 수 있고, 키보드의 키를 누르는 것일 수 있다. 하나의 이벤트 리스너는 3개의 파라미터를 포함하고 있고, 다음과 같은 문법을 사용할 수 있다.
```
<element>.addEventListener(<eventName>, <callbackFunction>, {capture : boolean} );
- element: 이벤트 리스너가 적용될 요소
- eventName: 
- callbackFunction: 이벤트가 발생한 후에 작동하는 function
- capture:boolean 
	- event capturing: 가장 가까운 요소부터 가장 먼 요소로 전파되는 프로세스
		-  bubbling과는 반대다. 
			- child div를 클릭하면 
				- child function > parent function > grandParent function 
	- event bubbling : 반대로 가장 먼 요소부터 가장 가까운 요소로 전파되는 프로세스
		- child div를 클릭하면,  그걸 포함하고 있는 Parent div, 그걸 포함하고 있는 GrandParent div까지 클릭됨
			- 그럼  event 수행 순서는 다음과 같다 
				- child functon > parent function > grand Parent Function
```
## References

- https://developer.mozilla.org/



> [!NOTE] 단어 찾기
>  * propagate
> 	 : to produce a new plant using a parent plant
>   e.g) Most house plants can be propated from stem cuttings
	  
  
  
