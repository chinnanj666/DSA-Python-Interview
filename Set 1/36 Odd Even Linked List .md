### Problem Description 

Given the head of a singly linked list, group all the nodes with odd indices together followed by the nodes with even indices, and return the reordered list.

The first node is considered odd, and the second node is even, and so on.

Note that the relative order inside both the even and odd groups should remain as it was in the input.

You must solve the problem in O(1) extra space complexity and O(n) time complexity.

 

Example 1:


Input: head = [1,2,3,4,5]
Output: [1,3,5,2,4]
Example 2:


Input: head = [2,1,3,5,6,4,7]
Output: [2,3,6,7,1,5,4]
 

Constraints:

The number of nodes in the linked list is in the range [0, 104].
-106 <= Node.val <= 106


```

class Solution:
    def oddEvenList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if not head or not head.next:
            return head;
        i = 1;
        curr = head;
        dummy = ListNode();
        odd = even = None; even_link = head.next;
        
        while curr:
            
            if (i&1) == 1:
                if odd:
                    odd.next = curr;
                odd = curr;
            else:
                if even:
                    even.next = curr;
                even = curr;
            curr = curr.next;
            i += 1;
        odd.next  = even_link;
        even.next = None;
        
        return head;
            
  
```
