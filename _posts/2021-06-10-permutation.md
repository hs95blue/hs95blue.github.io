---
layout: post
title: "[알고리즘] 순열 알고리즘의 이해"
tags: [알고리즘, permutation, 순열, Tips]
featured_image_thumbnail:
featured_image: assets/images/posts/2019/desk.jpg
featured: true
hidden: true
---

## 순열이란?  

<br>

> n개의 수 중에서 r개의 숫자를 모든 순서대로 뽑는 경우  

```java
/*

input : [1, 2, 3]이라는  3개의 숫자에서 2개의 숫자를 뽑는 경우

output : 

[1, 2]
[1, 3]
[2, 1]
[2, 3]
[3, 1]
[3, 2]
*/
```
이렇게 6개가 된다.

## 순열 알고리즘  


> 순열 알고리즘에는 2가지 방법이 있다.  

1. Swap을 이용한 순열 => 순서보장이 안됨.  
2. Visited 배열을 이용한 순열 => 순서가 보장됨. 사전식 배열[^1]  
   
[^1]: 규칙이 있는 배열.

## 1.Swap을 이용한 순열  

첫번째는 swap 메소드를 만들어 배열들의 값을 직접 바꾸는 방법이다.  

배열의 첫 값부터 순서대로 하나씩 바꾸며 모든 값을 한번씩 swap한다.  

depth를 기준 인덱스로 해 depth보다 인덱스가 작은 값들은 그대로 고정하고  

depth보다 인덱스가 큰 값들만 가지고 다시 swap을 진행한다.  

![Swap 방식](/assets/images/posts/2021/swap.png)

> 간단하고 깔끔하지만 순서가 보장되지 않는다.  


### Code
```java
/**
 * 순열 : n 개 중에서 r 개를 순서있게 뽑기
 * 시간복잡도: O(n!)
 */

public class Permutation {
    public static void main(String[] args) {
        int n = 3;
        int[] arr = {1, 2, 3};
        int[] output = new int[n];
        boolean[] visited = new boolean[n];

       // perm(arr, output, visited, 0, n, 3);
        System.out.println();
        permutation(arr, 0, n, 3);
    }

    // 사전순으로 순열 구하기
	/*
	 * // 사용 예시: perm(arr, output, visited, 0, n, 3); static void perm(int[] arr,
	 * int[] output, boolean[] visited, int depth, int n, int r) { if (depth == r) {
	 * print(output, r); return; }
	 * 
	 * for (int i = 0; i < n; i++) { if (visited[i] != true) { visited[i] = true;
	 * output[depth] = arr[i]; perm(arr, output, visited, depth + 1, n, r);
	 * visited[i] = false; } } }
	 */

    // 순열 구하기
    // 사용 예시: permutation(arr, 0, n, 4);
    static void permutation(int[] arr, int depth, int n, int r) {
        if (depth == r) {
            print(arr, r);
            return;
        }

        for (int i = depth; i < n; i++) {
            swap(arr, depth, i);
            permutation(arr, depth + 1, n, r);
            swap(arr, depth, i);
        }
    }

    static void swap(int[] arr, int depth, int i) {
        int temp = arr[depth];
        arr[depth] = arr[i];
        arr[i] = temp;
    }

    // 배열 출력
    static void print(int[] arr, int r) {
        for (int i = 0; i < r; i++)
            System.out.print(arr[i] + " ");
        System.out.println();
    }
}
```  

### 알아볼 것  

- DFS알고리즘?
- 재귀함수
- 재귀함수가 도저히 이해가안돼.,,.,.,.,.,.,.,낼 해야지.








