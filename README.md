# LeetcOdyssey
Notes on solutions of some classic problem from Leetcode

# Index

- [Linked List](#linked-list)
  - [Reverse Linked List](#reverse-linked-list)

# Linked List
## Reverse Linked List
Description: 

Given the `head` of a singly linked list, reverse the list, and return the reversed list.

Example:

```
Input: head = [1,2,3,4,5] 
Output: [5,4,3,2,1]
```

Basic ideas:

Prepend a dummy node `prev` to the list, pointing to the `head` node (`prev -> head`). We maintain a reversed part of the list (from `prev.next` to `cur`, both sides inclusive) during processing, and we iteratively put the next node of cur (`cur.next`) to the head of the reversed part (and modify the pointers accordingly) to preserve the ordering.

Inside the loop, do the following things:
1.  record the head of reversed part (`temp`).
2.  make `prev` points to the `cur.next` (new head of reversed part).
3.  `cur.next` moved to the head, make `cur.next.next` the next node of `cur`.
4.  make previous head of reversed part (`temp`) the next node of new head (`prev.next`).


```java
public ListNode reverseList(ListNode head) {
    // Prepend a dummy node
    ListNode prev = new ListNode(0), cur = head;
    prev.next = head;
    while (cur != null && cur.next != null) {
        ListNode temp = prev.next;
        prev.next = cur.next;
        cur.next = cur.next.next;
        prev.next.next = temp;
    }
    return prev.next;
}
```
