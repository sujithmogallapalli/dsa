## Problem
Given the head of a singly linked list, reverse the list, and return the reversed list.

## Sample
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]

## Approaches
### Approach 1 - Two pointer technique
- Initialize two variables prev, temp to maintain previous element and current element
- Initially prev should be null as there won't be any previous element for 1st element
- Traverse through linked list
  - Traverse until head != null
  - Assign current element next value with prev value
  - move to next element
- Return the prev reference as this will store the last element on last element
- Time complexity - O(n), Space complexity - O(1)
#### Pitfalls
- Here, head will be null on last iteration
- We need to return prev

## Approach 2 - Recursive approach with back tracking
- Base condition: if head is null or head.next == null we will return head
  - This step ensures we will be getting last node as head (starting point for reverse list)
- add recursive calls until the head reaches last node
- Assign the next of next element of current one with the current element address
- Assign the next element of current one with null to avoid double linkage
- Time complexity = O(n), Space complexity - O(n) (Recursive calls)

#### Pitfalls
- Don't forget to assign current element with null or else it will ended up with double links between each one

## Codes
### Two pointer technique
```java
public ListNode reverseList(ListNode head) {
    ListNode temp, prev = null;
    while (head != null) {
        temp = head;
        head = head.next;
        temp.next = prev;
        prev = temp;
    }
    return prev;
}
```
### Recursive approach with back tracking
```java
public ListNode reverseList(ListNode head) {
    if (head == null|| head.next == null)
        return head;
    ListNode node = reverseList(head.next);
    head.next.next = head;
    head.next = null;
    return node;
}
```