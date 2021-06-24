---
layout: post
title: '[Data Structure] Stack & Queue'
tags: [Spring, 스프링, Stack & Queue, Data Structure]
featured_image_thumbnail:
featured_image: assets/images/posts/2021/Spring.png
featured: true
# hidden: true
---

## Stack & Queue

### 스택  
> 입력/출력이 한 방향으로 제한  

- **LIFO**(Last In First Out) 

### 언제 사용?  
- 함수의 콜스택
- 문자열 역순 출력
- 연산자 후위표기법  

### 기능  
- push()  
- pop()  
- isEmpty()  
- isFull()  

push와 pop할 때는 해당 위치를 알고 있어야 하므로 기억하고 있는 '**스택 포인터(SP)**'가 필요함

스택 포인터는 **다음 값이 들어갈 위치**를 가리키고 있음 (처음 기본값은 -1)
```java
private int sp = -1;
```
##### push
```java
public void push(Object o) {
    if(isFull(o)) {
        return;
    }
    
    stack[++sp] = o;
}
```
> 스택 포인터가 **최대 크기**와 같으면 return    
> 아니면 스택의 **최상위 위치**에 값을 넣음.


##### pop
```java
public Object pop() {
    
    if(isEmpty(sp)) {
        return null;
    }
    
    Object o = stack[sp--];
    return o;
    
}
```
> 스택 포인터가 0이되면 null로 return  
> 아니면 스택의 최상위 위치값을 꺼내옴   

##### isEmpty
```java
private boolean isEmpty(int cnt) {
    return sp == -1 ? true : false;
}
```
> 입력값이 최초 값과 같다면 true 아니면 false  

  
##### isFull
```java
private boolean isFull(int cnt) {
    return sp + 1 == MAX_SIZE ? true : false;
}
```
> 스택포인터 값 +1이 MAX_SIZE와 같으면 true 아니면 false  

### 동적 배열 스택

> 위처럼 구현하면 최대크기가 존재. 최대크기가 없는 스택을 만들어보자  

- **arrycopy**를 이용한 동적배열 사용  
```java
public void push(Object o) {
    
    if(isFull(sp)) {
        
        Object[] arr = new Object[MAX_SIZE * 2];
        System.arraycopy(stack, 0, arr, 0, MAX_SIZE);
        stack = arr;
        MAX_SIZE *= 2; // 2배로 증가
    }
    
    stack[sp++] = o;
}
```
> 만약 스택이 다 차있으면, 배열 복사를 통해 값을 복사해서 넣어주고 MAX_SIZE를 2배로 초기화 해준다.  

### 연결리스트로 구현할 수도 있다.  

```java
public class Node {

    public int data;
    public Node next;

    public Node() {
    }

    public Node(int data) {
        this.data = data;
        this.next = null;
    }
}
public class Stack {
    private Node head;
    private Node top;

    public Stack() {
        head = top = null;
    }

    private Node createNode(int data) {
        return new Node(data);
    }

    private boolean isEmpty() {
        return top == null ? true : false;
    }

    public void push(int data) {
        if (isEmpty()) { // 스택이 비어있다면
            head = createNode(data);
            top = head;
        }
        else { //스택이 비어있지 않다면 마지막 위치를 찾아 새 노드를 연결시킨다.
            Node pointer = head;

            while (pointer.next != null)
                pointer = pointer.next;

            pointer.next = createNode(data);
            top = pointer.next;
        }
    }

    public int pop() {
        int popData;
        if (!isEmpty()) { // 스택이 비어있지 않다면!! => 데이터가 있다면!!
            popData = top.data; // pop될 데이터를 미리 받아놓는다.
            Node pointer = head; // 현재 위치를 확인할 임시 노드 포인터

            if (head == top) // 데이터가 하나라면
                head = top = null;
            else { // 데이터가 2개 이상이라면
                while (pointer.next != top) // top을 가리키는 노드를 찾는다.
                    pointer = pointer.next;

                pointer.next = null; // 마지막 노드의 연결을 끊는다.
                top = pointer; // top을 이동시킨다.
            }
            return popData;
        }
        return -1; // -1은 데이터가 없다는 의미로 지정해둠.

    }

}
```