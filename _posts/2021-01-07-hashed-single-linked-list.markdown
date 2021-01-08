---
title: "해쉬 단일 연결 리스트"
layout: post
date: 2021-01-07 22:10
tag: DataStructure
headerImage: true
projects: true
hidden: true # don't count this post in blog pagination
description: "This is a simple and minimalist template for Jekyll."
category: project
author: Yun
externalLink: false
---

# 해쉬 단일 연결 리스트
## 구현
- 구조체와 해쉬 테이블  
-100개의 원소를 가지는 배열을 생성하고 해쉬 함수는 나머지 연산으로 구현  
-해쉬 값 별로 연결리스트 구성(충돌을 피할 수 있음)  
```c
struct InfoNode {
    int key;
    struct InfoNode* next;
};
struct Table {
    struct InfoNode tbl[100];
};
int hashFunc(int key) {
    return key % 100;
}
```
![hashTable](https://bro-o.github.io/assets/images/hashTable.PNG)

- 삽입  
-동일한 키 값이 있는지 확인  
-없으면 알맞은 해쉬 값의 뒤의 리스트에 노드 삽입(정렬해서)
```c
struct InfoNode* createNode(int key) {
    struct InfoNode* newNode;

    newNode = (struct InfoNode*)malloc(sizeof(struct InfoNode));
    newNode->key = key;
    newNode->next = NULL;

    return newNode;
}
void insertNext(struct InfoNode** curr, int key) {
    struct InfoNode* newNode;
    newNode = createNode(key);
    newNode->next = (*curr)->next;
    (*curr)->next = newNode;
}
void insertTable(struct Table* t, int key) {
    int hKey = hashFunc(key);
    if (searchTable(t, key) != NULL) {
        printf("같은 키가 있습니다.\n");
    }
    else {
        struct InfoNode* node = &(t->tbl[hKey]);
        if (node->next == NULL) {
            (t->tbl[hKey]).key = key;
        }
        while (node->next != NULL && node->next->key <= key) {
            node = node->next;
        }    
        insertNext(&node, key);
    }
}
```

- 삭제
```c
char* deleteTable(struct Table* t, int key) {
    int hKey = hashFunc(key);

    struct InfoNode* node = (t->tbl[hKey]).next;
    while (node != NULL) {
        if (node->key == key) {

            node->key = 0;

            return node->key;
        }
        node = node->next;
    }
    return NULL;
}
```

- 검색
```c
char* searchTable(struct Table* t, int key) {
    int hKey = hashFunc(key);

    if ((t->tbl[hKey]).key == key) {
        return(t->tbl[hKey]).key;
    }
    else {
        struct InfoNode* node = (t->tbl[hKey]).next;
        while (node != NULL) {
            if (node->key == key) {
                return node->key;
            }
            node = node->next;
        }
    }
    return NULL;
}
```
- 출력
```c
void printTable(struct Table* t) {
    struct InfoNode* node;
    for (int i = 0; i < 100; i++) {
        node = (t->tbl[i]).next;
        printf("[%d]->", i);
        while (node != NULL) {
            printf("%d->", node->key);
            node = node->next;
        }
        printf("NULL\n");
    }
}
```

## 실행
![hashList](https://bro-o.github.io/assets/images/hashList.PNG)
