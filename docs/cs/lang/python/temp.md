# 📝 python学习知识点串联（gpt生成）

> **📅 日期：** 2026-07-12，以后要用的话记得搭配标签等别的功能
> **🏷️ 标签：** #python #核心语法 #底层逻辑
 有待自己吸收修改与总结
---

# 1. 整体区别

| 对比项 | C 语言 | Python |
|---|---|---|
| 类型系统 | 静态类型，变量声明时确定类型 | 动态类型，运行时确定类型 |
| 编译/解释 | 编译型语言 | 解释型语言 |
| 语句块 | 用 `{}` 表示代码块 | 用缩进表示代码块 |
| 行结束 | 通常用 `;` | 通常不用 `;` |
| 内存管理 | 手动管理较多，如 `malloc/free` | 自动垃圾回收 |
| 指针 | 有显式指针和地址操作 | 没有 C 风格指针 |
| 运行入口 | `main()` 函数 | 通常用 `if __name__ == "__main__":` |

---

# 2. 变量定义

## C 语言

C 语言需要先声明变量类型：

```c
int a = 10;
double b = 3.14;
char c = 'A';
```

变量类型固定：

```c
int x = 10;
x = 3.14;  // 会发生类型转换，可能丢失精度
```

---

## Python

Python 不需要声明类型：

```python
a = 10
b = 3.14
c = "A"
```

变量本质上是“名字”绑定到对象：

```python
x = 10
x = 3.14
x = "hello"
```

这是允许的。

---

## 对比

| 项目 | C | Python |
|---|---|---|
| 是否需要声明类型 | 需要 | 不需要 |
| 变量类型能否改变 | 一般不能 | 可以 |
| 示例 | `int a = 10;` | `a = 10` |

---

# 3. 基本数据类型

## C 常见类型

```c
int
float
double
char
long
short
```

例如：

```c
int age = 18;
double score = 95.5;
char ch = 'A';
```

---

## Python 常见类型

```python
int
float
str
bool
list
tuple
dict
set
```

例如：

```python
age = 18
score = 95.5
name = "Tom"
flag = True
```

Python 中没有单独的 `char` 类型，一个字符也是字符串：

```python
ch = "A"
```

---

# 4. 代码块：大括号 vs 缩进

## C 语言

```c
if (x > 0) {
    printf("positive\n");
}
```

C 用 `{}` 表示代码块。

---

## Python

```python
if x > 0:
    print("positive")
```

Python 用缩进表示代码块。

错误示例：

```python
if x > 0:
print("positive")  # 缩进错误
```

---

# 5. 数组、列表、元组、字典

这是 C 转 Python 时最重要的一部分。

---

## 5.1 C 数组

```c
int arr[5] = {1, 2, 3, 4, 5};
```

特点：

1. 长度固定
2. 类型固定
3. 内存连续
4. 用下标访问

```c
printf("%d\n", arr[0]);
```

---

## 5.2 Python 列表 list

Python 中最接近 C 数组的是 **列表 list**：

```python
arr = [1, 2, 3, 4, 5]
```

访问元素：

```python
print(arr[0])
```

修改元素：

```python
arr[0] = 100
```

添加元素：

```python
arr.append(6)
```

删除元素：

```python
arr.remove(3)
```

---

## C 数组 vs Python list

| 对比项 | C 数组 | Python list |
|---|---|---|
| 长度 | 通常固定 | 可变 |
| 类型 | 一般统一 | 可混合 |
| 访问方式 | 下标 | 下标 |
| 是否可修改 | 可以 | 可以 |
| 内存 | 连续存储具体数据 | 存对象引用 |

Python 列表可以混合类型：

```python
a = [1, "hello", 3.14, True]
```

而 C 数组通常不能这样：

```c
int a[3] = {1, 2, 3};
```

---

## 5.3 Python 元组 tuple

元组类似“不可修改的列表”。

```python
t = (1, 2, 3)
```

访问：

```python
print(t[0])
```

不能修改：

```python
t[0] = 100  # 报错
```

---

## 元组可以理解为 C 里的只读数组

类似：

```c
const int arr[3] = {1, 2, 3};
```

但只是类比，并不完全等价。

---

## 5.4 Python 字典 dict

字典是键值对结构：

```python
student = {
    "name": "张三",
    "age": 18,
    "score": 95
}
```

访问：

```python
print(student["name"])
print(student["age"])
```

修改：

```python
student["age"] = 19
```

新增：

```python
student["city"] = "北京"
```

---

## 字典类似什么？

在 C 中可以类比：

1. 哈希表
2. 结构体
3. 键值映射表

例如 C 结构体：

```c
struct Student {
    char name[20];
    int age;
    int score;
};
```

Python 字典：

```python
student = {
    "name": "Tom",
    "age": 18,
    "score": 90
}
```

区别是：

- C 结构体字段固定
- Python 字典可以动态增加键值

---

## 5.5 Python 集合 set

集合用于存储不重复元素：

```python
s = {1, 2, 3, 3, 3}
print(s)  # {1, 2, 3}
```

集合特点：

1. 无序
2. 不重复
3. 不能通过下标访问

集合运算：

```python
a = {1, 2, 3}
b = {3, 4, 5}

print(a | b)  # 并集
print(a & b)  # 交集
print(a - b)  # 差集
```

---

# 6. Python 中有没有数组？

严格来说，Python 内置最常用的是 `list`，但它不是 C 那种原生数组。

如果你想用更接近 C 数组的结构，可以用：

## 6.1 array 模块

```python
from array import array

a = array('i', [1, 2, 3, 4])
```

这里 `'i'` 表示整数类型。

---

## 6.2 NumPy 数组

科学计算中常用：

```python
import numpy as np

a = np.array([1, 2, 3, 4])
```

NumPy 数组更接近 C 的数组：

- 类型统一
- 存储紧凑
- 运算速度快
- 支持矩阵运算

---

# 7. 指针与地址

这是 C 和 Python 最大的差异之一。

---

## 7.1 C 语言指针

C 中可以取地址：

```c
int a = 10;
int *p = &a;
```

访问指针指向的值：

```c
printf("%d\n", *p);
```

修改：

```c
*p = 20;
```

此时：

```c
a == 20
```

---

## 7.2 Python 没有 C 风格指针

Python 不能这样写：

```python
p = &a   # 错误
*p = 20 # 错误
```

Python 没有：

```c
&
*
```

这种地址和解引用操作。

---

## 7.3 Python 中的变量更像“引用”

Python 变量可以理解为“名字指向对象”。

```python
a = [1, 2, 3]
b = a
```

这时 `a` 和 `b` 指向同一个列表。

```python
b[0] = 100
print(a)  # [100, 2, 3]
```

因为它们引用的是同一个对象。

---

## 7.4 Python 查看对象身份

Python 可以用 `id()` 查看对象标识：

```python
a = [1, 2, 3]
b = a

print(id(a))
print(id(b))
```

如果相同，说明它们指向同一个对象。

但注意：

> `id()` 不是给你做 C 指针运算用的地址。

---

## 7.5 可变对象与不可变对象

Python 中很重要的概念是：

| 类型 | 是否可变 |
|---|---|
| int | 不可变 |
| float | 不可变 |
| str | 不可变 |
| tuple | 不可变 |
| list | 可变 |
| dict | 可变 |
| set | 可变 |

例如：

```python
a = 10
b = a
b = 20

print(a)  # 10
```

因为整数不可变，`b = 20` 是让 `b` 指向新对象，不影响 `a`。

但是：

```python
a = [1, 2, 3]
b = a
b[0] = 100

print(a)  # [100, 2, 3]
```

列表可变，所以修改内容会影响所有引用它的变量。

---

# 8. 循环：for 和 while

---

## 8.1 while 循环

### C 语言

```c
int i = 0;

while (i < 5) {
    printf("%d\n", i);
    i++;
}
```

### Python

```python
i = 0

while i < 5:
    print(i)
    i += 1
```

区别：

- Python 条件后面要加 `:`
- Python 没有 `i++`
- Python 使用缩进表示循环体

---

## 8.2 for 循环

### C 语言

```c
for (int i = 0; i < 5; i++) {
    printf("%d\n", i);
}
```

### Python

Python 的 `for` 更像“遍历”：

```python
for i in range(5):
    print(i)
```

`range(5)` 产生：

```python
0, 1, 2, 3, 4
```

如果想从 1 到 5：

```python
for i in range(1, 6):
    print(i)
```

如果想步长为 2：

```python
for i in range(0, 10, 2):
    print(i)
```

输出：

```text
0
2
4
6
8
```

---

## 8.3 遍历数组/列表

### C 语言

```c
int arr[5] = {10, 20, 30, 40, 50};

for (int i = 0; i < 5; i++) {
    printf("%d\n", arr[i]);
}
```

### Python

```python
arr = [10, 20, 30, 40, 50]

for x in arr:
    print(x)
```

如果需要下标：

```python
for i, x in enumerate(arr):
    print(i, x)
```

---

## 8.4 break 和 continue

C 和 Python 都有：

### C

```c
for (int i = 0; i < 10; i++) {
    if (i == 5) break;
    if (i == 2) continue;
    printf("%d\n", i);
}
```

### Python

```python
for i in range(10):
    if i == 5:
        break
    if i == 2:
        continue
    print(i)
```

---

# 9. 条件语句

## C 语言

```c
if (x > 0) {
    printf("positive\n");
} else if (x == 0) {
    printf("zero\n");
} else {
    printf("negative\n");
}
```

---

## Python

```python
if x > 0:
    print("positive")
elif x == 0:
    print("zero")
else:
    print("negative")
```

注意：

- Python 是 `elif`
- 不是 `else if`
- 条件后面加 `:`
- 不用 `{}`

---

# 10. 字符串操作

---

## 10.1 C 字符串

C 字符串本质是字符数组，以 `'\0'` 结尾：

```c
char s[] = "hello";
```

字符串函数需要头文件：

```c
#include <string.h>
```

常见操作：

```c
strlen(s);
strcpy(dest, src);
strcmp(a, b);
strcat(a, b);
```

---

## 10.2 Python 字符串

Python 字符串是 `str` 对象：

```python
s = "hello"
```

长度：

```python
len(s)
```

访问字符：

```python
s[0]  # 'h'
```

切片：

```python
s[1:4]  # 'ell'
```

拼接：

```python
s = "hello" + " world"
```

查找：

```python
s.find("lo")
```

替换：

```python
s.replace("hello", "hi")
```

分割：

```python
"192.168.1.1".split(".")
```

结果：

```python
["192", "168", "1", "1"]
```

---

## 10.3 Python 字符串不可修改

```python
s = "hello"
s[0] = "H"  # 报错
```

正确做法：

```python
s = "H" + s[1:]
print(s)  # Hello
```

---

## 10.4 格式化输出

### C

```c
printf("age = %d, score = %.2f\n", age, score);
```

### Python

推荐 f-string：

```python
print(f"age = {age}, score = {score:.2f}")
```

---

# 11. 函数

---

## 11.1 C 语言函数

```c
int add(int a, int b) {
    return a + b;
}
```

调用：

```c
int result = add(3, 5);
```

---

## 11.2 Python 函数

```python
def add(a, b):
    return a + b
```

调用：

```python
result = add(3, 5)
```

---

## 对比

| 项目 | C | Python |
|---|---|---|
| 定义关键字 | 无，直接写返回类型 | `def` |
| 参数类型 | 通常要写 | 不写 |
| 返回类型 | 通常要写 | 不写 |
| 代码块 | `{}` | 缩进 |
| 返回 | `return` | `return` |

---

## 11.3 Python 函数可以返回多个值

Python 可以这样：

```python
def calc(a, b):
    return a + b, a - b, a * b
```

接收：

```python
x, y, z = calc(10, 3)
```

实际上返回的是一个元组：

```python
(13, 7, 30)
```

C 中如果想返回多个值，通常需要：

1. 使用指针参数
2. 使用结构体
3. 使用数组

例如 C 里用指针返回多个结果：

```c
void calc(int a, int b, int *sum, int *diff) {
    *sum = a + b;
    *diff = a - b;
}
```

---

# 12. 函数参数传递差异

---

## C 语言

C 默认是值传递：

```c
void change(int x) {
    x = 100;
}

int main() {
    int a = 10;
    change(a);
    printf("%d\n", a); // 10
}
```

如果要修改外部变量，需要指针：

```c
void change(int *x) {
    *x = 100;
}
```

---

## Python

Python 传递的是“对象引用”。

对于不可变对象：

```python
def change(x):
    x = 100

a = 10
change(a)
print(a)  # 10
```

对于可变对象：

```python
def change(lst):
    lst[0] = 100

a = [1, 2, 3]
change(a)
print(a)  # [100, 2, 3]
```

所以可以简单理解为：

> Python 不能通过给参数重新赋值来改变外部变量，但可以修改传入的可变对象内部内容。

---

# 13. 主函数 main

---

## C 语言

C 程序通常从 `main()` 开始执行：

```c
#include <stdio.h>

int main() {
    printf("Hello\n");
    return 0;
}
```

---

## Python

Python 没有强制的 `main()` 函数。

最简单的 Python 文件：

```python
print("Hello")
```

直接运行就会执行。

---

## Python 常见主入口写法

```python
def main():
    print("Hello")

if __name__ == "__main__":
    main()
```

含义：

- 当这个文件被直接运行时，执行 `main()`
- 当这个文件被其他文件导入时，不自动执行 `main()`

例如：

```python
if __name__ == "__main__":
    main()
```

可以理解为 Python 里的“程序入口保护”。

---

# 14. 头文件、include 和 import

---

## C 语言

```c
#include <stdio.h>
#include <string.h>
```

`#include` 是预处理阶段把头文件内容包含进来。

---

## Python

Python 使用 `import` 导入模块：

```python
import math

print(math.sqrt(16))
```

也可以：

```python
from math import sqrt

print(sqrt(16))
```

区别：

| C | Python |
|---|---|
| `#include <stdio.h>` | `import math` |
| 预处理包含文件 | 导入模块对象 |
| 编译前处理 | 运行时导入 |

---

# 15. 宏 macro

---

## C 语言宏

C 有预处理器：

```c
#define PI 3.14159
#define SQUARE(x) ((x) * (x))
```

使用：

```c
double area = PI * r * r;
int y = SQUARE(5);
```

宏是在编译前进行文本替换。

---

## Python 没有 C 语言这种宏

Python 中一般用：

### 1. 常量变量代替宏常量

```python
PI = 3.14159
```

Python 没有真正的常量限制，但习惯上用全大写表示常量。

---

### 2. 函数代替函数宏

C：

```c
#define SQUARE(x) ((x) * (x))
```

Python：

```python
def square(x):
    return x * x
```

---

### 3. 条件编译

C：

```c
#ifdef DEBUG
printf("debug mode\n");
#endif
```

Python 没有完全相同的预处理条件编译，一般用普通变量：

```python
DEBUG = True

if DEBUG:
    print("debug mode")
```

---

# 16. 注释

## C 语言

```c
// 单行注释

/*
多行注释
*/
```

---

## Python

```python
# 单行注释
```

多行字符串有时用于说明：

```python
"""
这是一段说明文字
通常用于文档字符串 docstring
"""
```

函数文档：

```python
def add(a, b):
    """
    返回 a 和 b 的和
    """
    return a + b
```

---

# 17. 输入输出

---

## C 输出

```c
printf("Hello\n");
```

## Python 输出

```python
print("Hello")
```

---

## C 输入

```c
int x;
scanf("%d", &x);
```

## Python 输入

```python
x = input("请输入：")
```

注意：`input()` 得到的是字符串。

如果需要整数：

```python
x = int(input("请输入整数："))
```

如果需要浮点数：

```python
x = float(input("请输入小数："))
```

---

# 18. 运算符差异

## 18.1 除法

### C

```c
int a = 5 / 2;  // 结果是 2
```

如果是整数除法，结果还是整数。

### Python

```python
print(5 / 2)   # 2.5
print(5 // 2)  # 2
```

Python 中：

| 运算符 | 含义 |
|---|---|
| `/` | 普通除法 |
| `//` | 整除 |
| `%` | 取余 |
| `**` | 幂运算 |

例如：

```python
print(2 ** 3)  # 8
```

C 中没有 `**`，通常用 `pow()`。

---

## 18.2 自增自减

C 有：

```c
i++;
i--;
```

Python 没有：

```python
i++  # 错误
```

Python 使用：

```python
i += 1
i -= 1
```

---

## 18.3 逻辑运算符

| C | Python |
|---|---|
| `&&` | `and` |
| `||` | `or` |
| `!` | `not` |

C：

```c
if (a > 0 && b > 0) {
    printf("ok\n");
}
```

Python：

```python
if a > 0 and b > 0:
    print("ok")
```

---

# 19. 结构体和类

---

## C 结构体

```c
struct Student {
    char name[20];
    int age;
};

struct Student s;
s.age = 18;
```

---

## Python 类

```python
class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age

s = Student("Tom", 18)
print(s.age)
```

Python 也可以用字典简单表示结构体：

```python
student = {
    "name": "Tom",
    "age": 18
}
```

---

# 20. 内存分配

---

## C

C 中可以手动分配和释放内存：

```c
int *p = malloc(sizeof(int) * 10);
free(p);
```

如果忘记 `free`，可能内存泄漏。

如果访问非法地址，可能段错误。

---

## Python

Python 通常不需要手动释放：

```python
a = [1, 2, 3]
```

当对象没有引用时，Python 会自动回收。

但是 Python 不是完全不需要关心资源，比如文件要关闭：

```python
f = open("a.txt", "r")
data = f.read()
f.close()
```

更推荐：

```python
with open("a.txt", "r") as f:
    data = f.read()
```

`with` 会自动关闭文件。

---

# 21. 异常处理

C 通常用返回值表示错误：

```c
FILE *fp = fopen("a.txt", "r");
if (fp == NULL) {
    printf("open failed\n");
}
```

Python 使用异常：

```python
try:
    f = open("a.txt", "r")
    data = f.read()
except FileNotFoundError:
    print("文件不存在")
finally:
    f.close()
```

更常见：

```python
try:
    with open("a.txt", "r") as f:
        data = f.read()
except FileNotFoundError:
    print("文件不存在")
```

---

# 22. 常见语法对照速查表

| 功能 | C 语言 | Python |
|---|---|---|
| 输出 | `printf("hi\n");` | `print("hi")` |
| 输入整数 | `scanf("%d", &x);` | `x = int(input())` |
| 定义整数 | `int x = 10;` | `x = 10` |
| 定义字符串 | `char s[] = "hi";` | `s = "hi"` |
| 数组 | `int a[3] = {1,2,3};` | `a = [1, 2, 3]` |
| 访问数组 | `a[0]` | `a[0]` |
| 字符串长度 | `strlen(s)` | `len(s)` |
| if | `if (x > 0) {}` | `if x > 0:` |
| else if | `else if` | `elif` |
| for | `for(i=0;i<n;i++)` | `for i in range(n):` |
| while | `while (i<n) {}` | `while i < n:` |
| 函数 | `int add(int a,int b)` | `def add(a, b):` |
| 返回值 | `return x;` | `return x` |
| 指针 | `int *p = &a;` | 无 C 风格指针 |
| 宏 | `#define PI 3.14` | `PI = 3.14` |
| 引入库 | `#include <stdio.h>` | `import math` |
| 主函数 | `int main(){}` | `if __name__ == "__main__":` |
| 注释 | `//` | `#` |

---

# 23. 一个完整例子对比

## C 语言版本

```c
#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int main() {
    int nums[5] = {1, 2, 3, 4, 5};
    int sum = 0;

    for (int i = 0; i < 5; i++) {
        sum = add(sum, nums[i]);
    }

    printf("sum = %d\n", sum);

    return 0;
}
```

---

## Python 版本

```python
def add(a, b):
    return a + b

def main():
    nums = [1, 2, 3, 4, 5]
    total = 0

    for x in nums:
        total = add(total, x)

    print(f"sum = {total}")

if __name__ == "__main__":
    main()
```

---

# 24. 从 C 转 Python 最需要注意的点

## 1. 不用写类型

C：

```c
int x = 10;
```

Python：

```python
x = 10
```

---

## 2. 不用分号

C：

```c
printf("hello\n");
```

Python：

```python
print("hello")
```

---

## 3. 不用大括号，用缩进

C：

```c
if (x > 0) {
    printf("ok\n");
}
```

Python：

```python
if x > 0:
    print("ok")
```

---

## 4. 没有指针，但有引用

C：

```c
int *p = &a;
```

Python 没有这种写法。

但：

```python
a = [1, 2, 3]
b = a
```

`a` 和 `b` 引用同一个列表。

---

## 5. Python 的 for 是遍历式

C：

```c
for (int i = 0; i < n; i++)
```

Python：

```python
for i in range(n):
    ...
```

遍历列表：

```python
for item in arr:
    ...
```

---

## 6. Python 字符串、元组、整数不可变

```python
s = "hello"
s[0] = "H"  # 错误
```

---

## 7. Python 列表、字典、集合可变

```python
a = [1, 2, 3]
a[0] = 100

d = {"name": "Tom"}
d["age"] = 18
```

---

# 25. 最后总结

如果用一句话概括：

> C 更接近底层，强调类型、内存、指针和编译；Python 更接近高级抽象，强调简洁、动态类型、容器和快速开发。

从 C 语言转 Python，可以这样记：

```text
C 数组        -> Python list / array / numpy array
C 只读数组    -> Python tuple
C 结构体      -> Python dict / class
C 指针        -> Python 没有显式指针，但变量是对象引用
C #define     -> Python 常量变量或函数
C main        -> Python 的 if __name__ == "__main__":
C for 循环    -> Python 的 for ... in ...
C 字符数组字符串 -> Python str
```

你如果已经学过 C，那么学 Python 时重点关注：

1. 缩进语法  
2. 动态类型  
3. list、tuple、dict、set  
4. 引用和可变/不可变对象  
5. Python 的函数和模块导入方式  

掌握这些后，Python 的基础语法就比较容易上手了。