## Problem
Design Linked list operations
- Add at head
- Add at tail
- Add at index
- Delete at index
- get element at index

## Codes
### Single linked list
```java
class Node {
    int val;
    Node next;

    Node(int val) {
        this.val = val;
        this.next = null;
    }
}

class MyLinkedList {

    int size;
    Node head;
    
    public MyLinkedList() {
        head = null;
        size = 0;
    }
    
    public int get(int index) {
        if (head == null || index < 0 || index > size - 1)
            return -1;
        
        Node node = head;
        int i = 0;
        while (i < index) {
            node = node.next;
            i++;
        }
        return node.val;
    }
    
    public void addAtHead(int val) {
        if (head == null)
            head = new Node(val);
        else {
            Node newNode = new Node(val);
            newNode.next = head;
            head = newNode;
        }
        size++;
    }
    
    public void addAtTail(int val) {
        if (head == null)
            head = new Node(val);
        else {
            Node newNode = new Node(val);
            Node node = head;
            while (node.next != null) {
                node = node.next;
            }
            node.next = newNode;
        }
        size++;
    }
    
    public void addAtIndex(int index, int val) {
        if (index < 0 || index > size)
            return;
        
        if (index == 0) {
            addAtHead(val);
        }
        else {
            Node node = head;
            Node newNode = new Node(val);
            int i = 0;
            while (i < index - 1) {
                node = node.next;
                i++;
            }

            newNode.next = node.next;
            node.next = newNode;
        }
        size++;
    }
    
    public void deleteAtIndex(int index) {
        if (head == null || index < 0 || index > size - 1)
            return;
        
        Node node = head;
        Node prev = null;

        if (index == 0){
             head = head.next;
            node.next = null;
        }
        else {
            int i = 0;
            while (i < index) {
                prev = node;
                node = node.next;
                i++;
            }
            prev.next = node.next;
            node.next = null;
        }
        size--;
    }
}
```