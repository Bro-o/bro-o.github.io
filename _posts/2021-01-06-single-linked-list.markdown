---
title: "단일 연결 리스트"
layout: post
date: 2020-12-19 22:10
tag: DataStructure
headerImage: true
projects: true
hidden: true # don't count this post in blog pagination
description: "This is a simple and minimalist template for Jekyll."
category: project
author: Yun
externalLink: false
---

# 단일 연결 리스트

## 구현
 - 구조체 선언
 데이터 변수 선언, 동일한 데이터 구조를 가리킬 수 있는 구조체 포인터 변수 포함
 ```c
 struct Node
 {
	int data;
	struct Node* next;
};
```

- 노드 생성
-데이터에 넣을 value라는 매개변수를 지정
-malloc으로 메모리를 할당
-데이터 값과 포인터를 지정해주고 노드를 반환
```c
struct Node* createNode(int value)
{
	struct Node* newNode;
	
	newNode = (struct Node*)malloc(sizeof(struct Node));
	newNode->data = value;
	newNode->next = NULL;
	
	return newNode;
}
```
![createNode](https://bro-o.github.io/assets/images/createNode.PNG)
- 노드 정렬 삽입
-리스트의 head를 가리키는 포인터와 데이터 값 value를 매개변수로 받음
-value를 이용해 새로운 노드를 만들고 리스트에 있는 값과 비교해 위치를 찾음
-새로운 노드의 포인터는 찾은 위치의 다음 노드를 가리키고, 찾은 위치의 포인터는 새로운 노드를 가리킴
```c
void  insertNode(struct Node* head, int  value)
{
	struct Node* curr = head;
	struct Node* newNode;

	newNode = createNode(value);

	while(curr->next != NULL && curr->next->data <= value){
		curr = curr->next;
	}
	
	newNode->next = curr->next;
	curr->next = newNode;
}
```
![insertNode](https://bro-o.github.io/assets/images/insertNode.PNG)
- 노드 검색
-리스트의 head를 가리키는 포인터와 찾는 데이터 값 value를 매개변수로 받음
-while 문으로 리스트의 끝까지 가면서 찾는 데이터가 있는지 확인
-있으면 그 노드를 가리키는 포인터 값을 반환
```c
struct Node* searchNode(struct Node* head, int  value)
{
	struct Node* curr;
	curr = head;
	
	while(curr!=NULL){
		if(curr->data == value)
			return curr;
		curr = curr->next;
	}
	
	return  NULL;
}
```
- 리스트 출력
```c
void  printList(struct Node* node)
{
	while(node != NULL){
		printf("[%d]->", node->data);
		node = node->next;
	}
	printf("NULL\n");
}
```
- 노드 삭제
-삭제할 노드를 searchNode함수를 이용하여 찾음
-찾은 노드의 이전 노드가 찾은 노드의 다음 노드를 가리킴
-free함수를 이용하여 메모리를 해제
```c
void  deleteNode(struct Node** phead, int  data)
{
	struct Node *prev, *curr;
	curr = searchNode(*phead, data);
	if(curr == NULL){
		printf("There is no data %d in the list.\n", data);
	}
	else{
		if(curr != *phead){
			prev = *phead;
		while(prev->next != curr){
			prev = prev->next;
		}
		prev->next = curr->next;
		free(curr);
		}
		else{
			*phead = curr->next;
		}
	}
}
```
![deleteNode](https://bro-o.github.io/assets/images/deleteNode.PNG)
-이중 포인터를 사용한 이유는 아래 그림처럼 main 함수에 있는 head와 호출된 함수의 head가 같은 곳을 가리키지만, 그 값을 보유하는 메모리 위치는 다름
-curr->next를 하면 이 때 변경되는 것은 호출된 함수의 head이고 main함수의 head의 값은 변하지 않음
![headincalledNode](https://bro-o.github.io/assets/images/headincalled.PNG)
![phead](https://bro-o.github.io/assets/images/phead.PNG)

## 실행
![print](https://bro-o.github.io/assets/images/linkedList.PNG)
