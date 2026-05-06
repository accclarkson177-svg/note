# 📝 指针链表知识点串联

> **📅 日期：** 2026-05-03，以后要用的话记得搭配标签等别的功能
> **🏷️ 标签：** #C语言 #核心语法 #底层逻辑

---

## 💡 0. 格式示范 (Distill)
*用一句话或一段精炼的话总结这个知识点的本质，注重逻辑联系。*
- **概念拆解：** - **核心痛点/易错点：** ## 💻 2. 代码示例 (Express)
*展示该概念的最简且完备的代码实现，剥离冗余逻辑。*

## 💡 1. 指针核心
### 数组与指针的等价性
一维，二维，etc，*&恒等式，a[0]

### swap函数的理解
```c
void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}
```
```c
 {
    *a = *(&i) = i  // 通过地址找回i
    *b = *(&j) = j  // 通过地址找回j
}
```

## 💡 1.5 一个等价写法
```c
//a->b   完全等于   (*a).b

struct Node {
    int data;
};

struct Node node;       // 定义普通变量
struct Node *p = &node; // 定义上面那个变量的指针，
//struct中的变量连续存放，p是起始地址（这里不是解引用）

// 下面三行效果完全一样
node.data = 10;
(*p).data = 10;
p->data = 10;    

```

## 💡 2. 链表模板
- ✅ 创建节点用 `malloc`
- ✅ 删除节点用 `free`
- ✅ 修改链表结构（增 / 删 / 改）都不需要重复 `malloc`
```c
#include <stdio.h>
#include <stdlib.h>  // 用于 malloc 申请内存

// 1. 定义一个【链表节点】
// 指向下一个节点的指针必要性，以后可能会有prev
struct Node {
    int data;               // 存数据
    struct Node* next;      // 存下一个节点的地址（单向链表只有后继）
};
```
注意这样定义的好处，就是他next只能存放下一个节点的地址

```c
// 2. 函数：向链表【尾部添加一个元素】
// 参数：头节点指针、要添加的数字
// 返回：一个struct Node类型的指针（指针指向头节点的地址）

//所以说这段程序里面，最开始的没连进去的新节点和原来的链表最终都指向了null
//我们要做的是修改结构
//不论用什么方式创建链表，都要在定义中明确null的位置
struct Node* addToTail(struct Node* head, int num) {
    // 第一步：申请一块新内存，创建新节点
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));  
    //固定句子，前面强制转换类型，malloc本身就是变成一个指针，前面甚至可以省略
    newNode->data = num;    //函数参数num的值存到这个指针参数表data里面去
    newNode->next = NULL;   //新的节点后面不要有东西

    // 情况1：链表是空的
    if (head == NULL) {
        return newNode;     // 新节点直接当头节点
    }

    // 情况2：链表已经有节点，找到最后一个节点
    struct Node* temp = head;
    while (temp->next != NULL) {
        temp = temp->next;  // 一直往后走
    }

    // 当后面没东西了，把newnode赋值给后面那个
    temp->next = newNode;

    return head;  // 返回头节点
}

//返回头节点即可，有头就能牵出全部

```
补充例子：比如我创建链表不用add这个函数，我直接在main里来
```c
// 创建头节点
struct Node* head = (struct Node*)malloc(sizeof(struct Node));
head->data = 10;
head->next = NULL;

// 创建第二个节点并接上去
struct Node* p2 = (struct Node*)malloc(sizeof(struct Node));
p2->data = 20;
p2->next = NULL;
head->next = p2;


```



```c
// 3.函数：删除链表的最后一个节点
// 参数：头节点指针
// 返回：新的头节点指针
struct Node* deleteTail(struct Node* head) {
    // 情况1：链表是空的，直接返回，啥也不做
    if (head == NULL) {
        return NULL;
    }

    // 情况2：链表只有1个节点，直接删掉它
    if (head->next == NULL) {
        free(head);  // 释放内存
        return NULL; // 链表变空了
    }

    // 情况3：链表有多个节点，找到【倒数第二个】节点
    struct Node* temp = head;
    // 循环找到：temp的下一个的下一个是NULL
    while (temp->next->next != NULL) {
        temp = temp->next;
    }

    // 现在 temp 就是【倒数第二个节点】
    // 1. 释放最后一个节点的内存
    free(temp->next);
    // 让链表接上
    temp->next = NULL;

    // 返回头节点（头没变）
    return head;
}//删除的本质：释放内存再修改结构（malloc之后一定要free）

```

```c
// 功能：删除连续重复的节点，相同数值只留一个
struct Node* removeDuplicates(struct Node* head) {
    // 链表为空，直接返回
    if (head == NULL) {
        return head;
    }

    // 当前节点 从 头节点 开始
    struct Node* current = head;

    // 遍历到最后一个节点
    while (current != NULL && current->next != NULL) {
        // 如果 当前节点 和 下一个节点 数据相同,
        // 这里涉及具体的数值，引入data，注意结构体有俩东西
        if (current->data == current->next->data) {
            // 这里先定义要删除的节点
            struct Node* gun = current->next;

            // 跳过要删除的节点
            current->next = current->next->next;

            // 释放内存（真正删除）
            free(gun);
        }
        else {
            // 不重复，就往后走
            current = current->next;
        }
    }

    return head;
}

```

```c
// 迭代法：反转链表，返回新的头节点
struct Node* reverseListIter(struct Node* head) {
    struct Node* prev = NULL;   // 前一个节点，初始为NULL（新链表的尾）
    struct Node* curr = head;   // 当前节点，从头开始,形参函数定义。
    struct Node* next = NULL;   // 临时保存下一个节点，防止断链

    while (curr != NULL) {
        next = curr->next;     // 1. 先保存下一个节点，不然断链
        curr->next = prev;     // 2. 反转当前节点的next指针，指向前一个节点
        prev = curr;           // 3. prev往前挪一步，到当前节点
        curr = next;           // 4. curr往前挪一步，到原来的下一个节点
    }

    // 循环结束时，prev就是新的头节点
    return prev;
}

```

```c
// 递归法：反转链表，返回新的头节点
struct Node* reverseListRecur(struct Node* head) {
    // 递归终止条件：链表为空或只有一个节点，直接返回
    if (head == NULL || head->next == NULL) {
        return head;
    }

    // 递归反转后面的链表，newHead是反转后的新头节点
    struct Node* newHead = reverseListRecur(head->next);

    // 关键反转步骤：
    // 让当前节点的下一个节点，指向当前节点自己
    head->next->next = head;
    // 断开当前节点原来的next指针，防止成环
    head->next = NULL;

    // 一直返回新的头节点，直到最外层调用
    return newHead;
}

```


```c

// 函数：遍历打印链表
void printList(struct Node* head) {
    struct Node* temp = head;
    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}
```

```c
// 4. 主函数
int main() {
    struct Node* head = NULL;  // 一开始链表是空的

    // 往链表里添加元素
    head = addToTail(head, 10);
    head = addToTail(head, 20);
    head = addToTail(head, 30);
    head = addToTail(head, 40);
//
加第一个元素 → 头变了 → 返回新头
加第二个元素 → 头没变 → 返回老头
加第三个元素 → 头没变 → 返回老头
加第四个元素 → 头没变 → 返回老头
...
//
    head = deleteTail(head);

    // 打印看结果
    printf("链表内容：");
    printList(head);

    return 0;
}
```

