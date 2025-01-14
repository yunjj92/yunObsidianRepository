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

<pre>
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
</pre>

<pre >
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
</pre>

---
## Questions

<!-- What remains for you to consider? --> 
- 


## Terms
<!-- Links to definition pages -->
- 


## References
<!-- Links to pages not referenced in the content -->
- 


