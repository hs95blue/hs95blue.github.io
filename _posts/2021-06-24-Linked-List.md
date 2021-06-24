---
layout: post
title:  "[Data Structure]Linked List"
tags: [ Jekyll, Development, Data Structure, Computer Science ]
featured_image_thumbnail:
featured_image: assets/images/posts/2018/11.jpg
featured: true
---

## Linked List  
> 연속적인 메모리 위치에 저장되지 않는 선형 데이터 구조  

- 반면에 **연속적인** 메모리 위치에 저장되는 선형데이터 구조는 배열  
- **포인터**를 사용해서 연결된다.  
- 각 엘리먼트를 **노드**라고 하고, 노드는 <m>데이터 필드</m>와 <m>다음노드에 대한 참조</m>를 포함한다.  

![LinkedList](/assets/images/posts/2021/LinkedList.png)  

### Why Linked List?  

> 배열로는 제한 사항이 좀 있다.  

1. 배열은 처음부터 **크기를 지정**해야한다.     
2. 새로운 요소를 삽입하려면 **비용**이 많이 든다.  
   - (넣고 싶은 위치에 있는 데이터를 뒤로 다 이동시키고 넣어야 하기 때문에. )  

### 장점  
1. 동적 크기  
   - 크기를 자유자재로 할당할 수 있다. 크기를 늘리고 싶으면 그냥 하나더 넣으면 되니까!    
2. 삽입/삭제 용이  
   - 삽입/삭제 할때 노드가 가리키는 포인터값만 변경하면 되니까!  

### 단점  
1. 임의로 액세스 허용불가.  
   - 첫번째 노드부터 순차적으로 요소에 액세스 해야한다.요소의 주소값은 **앞의 노드**에 있기 때문에!  
   - 이진탐색이 안됨.  
2. 포인터의 여분의 메모리 공간이 각 요소에 필요  
   - 데이터만 있는게 아니라 **포인터가 들어갈 공간**도 필요하다.  

노드 구현은 아래와 같이 데이터와 다음노드에 대한 참조로 나타낼 수 
있다.  
```java
  // A linked list node 
  struct Node 
  { 
    int data; 
    struct Node *next; 
  }; 
```

### Linked List를 만들어 보자!  

```java
    class LinkedList{
    
    Node head;

    static class Node {
        int data;
        Node next;
        Node(int d) { // 생성자
            data = d; next = null;
        }
    }

    public void printList() 
    { 
        Node n = head; 
        while (n != null) 
        { 
            System.out.print(n.data+" "); 
            n = n.next; 
        } 
    }

    public static void main(String[] args){

        LinkedList llist = new LinkedList();

        llist.head = new Node(1);
        Node second = new Node(2);
        Node third = new Node(3);

        /*
          llist.head        second              third 
             |                |                  | 
             |                |                  | 
         +----+------+     +----+------+     +----+------+ 
         | 1  | null |     | 2  | null |     |  3 | null | 
         +----+------+     +----+------+     +----+------+ 
        */
    
        llist.head.next = second; // 첫번째 노드에 두번째 노드 연결
        second.next = third; // 두번째 노드에 세번째 노드 연결
        
        /*
  
         llist.head        second              third 
            |                |                  | 
            |                |                  | 
        +----+------+     +----+------+     +----+------+ 
        | 1  |  o-------->| 2  |  o-------->|  3 | null | 
        +----+------+     +----+------+     +----+------+ 
        
        */
        llist.printList(); 
    }
}
```
