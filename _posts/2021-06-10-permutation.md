---
layout: post
title: "[알고리즘] 순열 알고리즘의 이해"
tags: [알고리즘, permutation, 순열, Tips]
featured_image_thumbnail:
featured_image: assets/images/posts/2019/desk.jpg
featured: true
# hidden: true
---

### 순열이란?  

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

### 순열 알고리즘  

> 순열 알고리즘에는 2가지 방법이 있다.  

1. Swap을 이용한 순열 => 순서보장이 안됨.  
2. Visited 배열을 이용한 순열 => 순서가 보장됨. 사전식 배열[^1]  
   
[^1]: 규칙이 있는 배열.

### 1.Swap을 이용한 순열  

첫번째는 swap 메소드를 만들어 배열들의 값을 직접 바꾸는 방법이다.  

배열의 첫 값부터 순서대로 하나씩 바꾸며 모든 값을 한번씩 swap한다.  

depth를 기준 인덱스로 해 depth보다 인덱스가 작은 값들은 그대로 고정하고  

depth보다 인덱스가 큰 값들만 가지고 다시 swap을 진행한다.  

![Swap 방식](/assets/images/posts/2021/swap.png)

> 간단하고 깔끔하지만 순서가 보장되지 않는다.  


### Pseudo Code
```java
//알고리즘이라고 어렵게 생각하지말고 직관적으로 어떻게 해왔는지 생각해보자
		//input : [1, 2, 3]
        //output :  각각 다른 순서의 숫자의 모든 경우 출력

		//1이 맨앞에 오게한다 swap(0,0)
			//2가 두번째 오게한다.3이 세번째 오게한다.swap(1,1)
			//출력한다.
			//3이 두번째 오게한다.2가 세번째 오게한다.swap(1,2)
			//출력한다.
		//2가 맨앞에 오게한다. swap(0,1)
			//1이 두번째오게한다,3이 세번째오게한다. swap(1,1)
		    //3이 두번째오게한다.1이 세번째 오게한다.swap(1,2)
			//출력한다.
		
		//같은 패턴으로 3이 맨앞으로 오게한 후 수행한다.
		
		//로직정리
		/* 
		 * IF depth가 r이면  
		 * 	출력한다.
		 * 아니면 
		 * Loop:
		 * 	어떤 숫자를 depth자리에 오게한다. -> swap(a, b)
		 * 	depth++ ,  1로 돌아간다.
		 * 	제자리로 돌려놓는다.
		 * END CODE
		 * 		 
		 */
```

### Java Code
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

#### 궁금증   

- DFS알고리즘?
- 재귀함수
- 재귀함수가 도저히 이해가안돼.,,.,.,.,.,.,.,낼 해야지.








