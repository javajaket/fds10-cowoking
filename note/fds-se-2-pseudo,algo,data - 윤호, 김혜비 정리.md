# Fastcampus 
## Frontend Dev SCHOOL
### Algorithm & Data structure

---
<!--
page_number: true
$size: A4
footer : fastcampus 프론트엔드 개발 스쿨, Wooyoung Choi, 2018
-->
## 5월 9일 수업정리

---
## Pseudocode

> 가짜코드: 프로그램이나 알고리즘이 수행할 내용을 인간이 이해할 수 있는 언어로 표현하는 것

> 정해진 형식은 없지만, 가급적 타인이 알아보기 쉽게 상세하고 친절하게 작성


---
### fizzbuzz

```
1. get integer from user ==> num, i == 1
2. WHILE i is less than or equal to num
3. if i is divisible by 15, print "fizz"
4. if i is divisible by 3, print "buzz"
5. if i is divisible by 5, print "fizzbuzz"
6. else, print i
```
> 순차적으로 실행되기 때문에 가장 먼저 공배수 처리! (line 3)

> 처리량이 많은 것을 우선 실행해서 프로그램의 전체 시간복잡성을 고려! (line 4,5)

---
## Algorithm
> Algorithm is a series of contained steps which you follow in order to achieve some goal, or to produce some output

> 목표를 달성하거나 결과물을 생산하기 위해 필요한 과정들

> Algorithm is focus on clarity
>> *Clarity : time complexity == big O notation  
  

---
## big O notation

1
log n
n
n log n
- 이정도까지만 활용, 밑으로는 사용 X

$n^2$
$n^3$
$2^n$
n!

> O(1) : constant
- 값에 대한 키 또는 인덱스를 알고 있을 경우 (Random Access)
> O(log n) : logarithmic
- 배열에서 값을 접근할 때 앞 또는 뒤에서 접근 선택이 가능할 경우 (순차적 접근)
> O(n): linear
- 자료의 수와 시도횟수가 1:1 관계인 경우 (반복문)

---
## Sort algorithms

- O($n^2$)
	- Bubble sort
	- Selection sort
	- Insertion sort : 간단한 자료는 사용
- O(n log n)
	- Merge sort
	- Heap sort
	- Quick sort : 무조건 퀵, 가장 빠름

---
## Data Structure


Tree - DOM rendering performance, reply
 - 브라우저가 파싱을 빠르고 효율적으로 할 수 있게 하기 위해선
HTML 페이지를 만들 때 트리구조를 잘 짜야함

> Binary Tree Search

	- Queue(BFS, Breadth First Search) : FIFO (enqueue, dequeue(shift))
	- Stack(DFS, Depth First Search)  : LIFO (push, pop)

> Linked List
    
	- 메모리에 선형으로 무작위로 저장하되, 값과 다음 행선지를 함께 저장하여 찾아감

> Tree

    - 상하관계를 구조화하기 위한 축약모델  (순위에 따라 정렬된)
	- 최상위 : Root, 같은 층 : Level (Root부터 0,1,2,3), 하위 개체 : Node, 화살표 : Edge
	- only two children --> Binary Tree
