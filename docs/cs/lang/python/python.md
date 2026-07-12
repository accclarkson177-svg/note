# python语法对比1

---

# 1. C 语言数组 vs Python 列表 list

## C 语言数组

在 C 语言中：

```c
int a[5] = {1, 2, 3, 4, 5};
```

特点：

1. 长度固定
2. 元素类型相同
3. 内存连续
4. 通过下标访问

```c
a[0]; // 第一个元素
```

---

## Python 列表 list

Python 中最接近 C 数组的是 **列表 list**：

```python
a = [1, 2, 3, 4, 5]
```

访问方式类似：

```python
print(a[0])   # 1
print(a[2])   # 3
```

但是 Python 列表比 C 数组灵活很多。

### Python 列表特点

#### 1. 长度可以变

```python
a = [1, 2, 3]
a.append(4)

print(a)  # [1, 2, 3, 4]
```

#### 2. 可以存不同类型的数据

```python
a = [1, "hello", 3.14, True]
```

在 C 语言中，一个数组通常只能存同一种类型，例如：

```c
int a[3];
char s[10];
```

但 Python 列表可以混合存储。

#### 3. 可以修改

```python
a = [1, 2, 3]
a[0] = 100

print(a)  # [100, 2, 3]
```

所以列表是 **可变对象**。

---

# 2. Python 元组 tuple

元组和列表很像，也是一组有顺序的数据。

```python
t = (1, 2, 3)
```

访问方式：

```python
print(t[0])  # 1
```

但是元组和列表最大的区别是：

> 元组创建之后不能修改。

例如：

```python
t = (1, 2, 3)
t[0] = 100
```

会报错：

```python
TypeError: 'tuple' object does not support item assignment
```

---

## 列表 list 和 元组 tuple 对比

| 特点 | list 列表 | tuple 元组 |
|---|---|---|
| 写法 | `[1, 2, 3]` | `(1, 2, 3)` |
| 是否有序 | 有序 | 有序 |
| 是否可通过下标访问 | 可以 | 可以 |
| 是否可修改 | 可以 | 不可以 |
| 长度是否可变 | 可以 | 不可以 |
| 用途 | 存放需要修改的数据 | 存放固定不变的数据 |

---

## 元组的例子

比如一个点的坐标：

```python
point = (3, 5)
```

表示：

```text
x = 3
y = 5
```

如果你不希望坐标被随便修改，可以用元组。

---

# 3. Python 字典 dict

字典是 Python 中非常重要的数据结构。

它类似于 C 语言里的：

- 结构体数组
- 哈希表
- key-value 映射

字典存储的是：

```text
键 key -> 值 value
```

例如：

```python
student = {
    "name": "张三",
    "age": 18,
    "score": 95
}
```

这里：

```text
"name"  -> "张三"
"age"   -> 18
"score" -> 95
```

访问字典里的数据：

```python
print(student["name"])   # 张三
print(student["age"])    # 18
```

---

## 和 C 数组的区别

C 数组通过数字下标访问：

```c
a[0]
a[1]
a[2]
```

Python 字典通过 key 访问：

```python
student["name"]
student["age"]
```

也就是说：

```python
list:  通过下标访问
dict:  通过键访问
```

---

## 字典可以修改

```python
student = {
    "name": "张三",
    "age": 18
}

student["age"] = 19
student["city"] = "北京"

print(student)
```

输出：

```python
{'name': '张三', 'age': 19, 'city': '北京'}
```

---

## 字典的特点

| 特点 | 说明 |
|---|---|
| 是否有序 | Python 3.7 之后保持插入顺序 |
| 访问方式 | 通过 key |
| 是否可修改 | 可以 |
| key 是否重复 | 不能重复 |
| value 是否重复 | 可以重复 |

例如：

```python
d = {
    "a": 1,
    "b": 2,
    "a": 3
}

print(d)
```

结果是：

```python
{'a': 3, 'b': 2}
```

因为 key `"a"` 重复了，后面的值覆盖前面的值。

---

# 4. Python 集合 set

集合 set 类似数学中的集合。

```python
s = {1, 2, 3}
```

特点：

1. 元素不重复
2. 无序
3. 可以用于去重
4. 可以做交集、并集、差集等操作

---

## set 例子：自动去重

```python
s = {1, 2, 2, 3, 3, 3}

print(s)
```

输出：

```python
{1, 2, 3}
```

---

## 集合运算

```python
a = {1, 2, 3}
b = {3, 4, 5}

print(a | b)  # 并集 {1, 2, 3, 4, 5}
print(a & b)  # 交集 {3}
print(a - b)  # 差集 {1, 2}
```

---

# 5. 字符串 str

Python 字符串类似 C 语言里的字符数组，但更高级。

C 语言中：

```c
char s[] = "hello";
```

Python 中：

```python
s = "hello"
```

访问字符：

```python
print(s[0])  # h
print(s[1])  # e
```

但是 Python 字符串不能修改。

```python
s = "hello"
s[0] = "H"
```

会报错。

如果想得到新字符串：

```python
s = "H" + s[1:]
print(s)  # Hello
```

---

# 6. 总结对比表

| Python 类型 | 写法 | 类似 C 中的什么 | 是否有序 | 是否可修改 | 访问方式 |
|---|---|---|---|---|---|
| list 列表 | `[1, 2, 3]` | 数组，但更灵活 | 有序 | 可修改 | 下标 |
| tuple 元组 | `(1, 2, 3)` | 固定数组/只读数组 | 有序 | 不可修改 | 下标 |
| dict 字典 | `{"name": "Tom"}` | 哈希表/键值表 | 保持插入顺序 | 可修改 | key |
| set 集合 | `{1, 2, 3}` | 数学集合/哈希集合 | 无序 | 可修改 | 不能用下标 |
| str 字符串 | `"hello"` | 字符数组 | 有序 | 不可修改 | 下标 |

---

# 7. 用 C 思维理解 Python 数据结构

你可以这样理解：

## list：动态数组

```python
a = [10, 20, 30]
```

类似：

```c
int a[] = {10, 20, 30};
```

但 Python 的 list 可以：

```python
a.append(40)
a.remove(20)
```

---

## tuple：不可修改的数组

```python
t = (10, 20, 30)
```

类似一个只读数组：

```c
const int t[] = {10, 20, 30};
```

---

## dict：用名字访问的数组

```python
student = {
    "name": "张三",
    "age": 18
}
```

比起：

```c
student[0]
student[1]
```

Python 可以写成：

```python
student["name"]
student["age"]
```

更直观。

---

## set：不允许重复的容器

```python
s = {1, 2, 3}
```

如果你加入重复元素：

```python
s.add(2)
```

集合里还是：

```python
{1, 2, 3}
```

---

# 8. 一个综合例子

假设我们要表示一个班级学生信息。

## 用列表存多个学生

```python
students = [
    {"name": "张三", "age": 18, "score": 90},
    {"name": "李四", "age": 19, "score": 85},
    {"name": "王五", "age": 18, "score": 92}
]
```

这里：

```python
students
```

是一个列表。

列表里的每个元素是一个字典。

访问第一个学生姓名：

```python
print(students[0]["name"])
```

输出：

```python
张三
```

访问第二个学生成绩：

```python
print(students[1]["score"])
```

输出：

```python
85
```

这相当于 C 语言中结构体数组的感觉：

```c
struct Student {
    char name[20];
    int age;
    int score;
};

struct Student students[3];
```

Python 写法更灵活。

---

# 9. 重点记忆

如果你刚从 C 语言转 Python，可以先记住：

```text
list  = 可变数组
tuple = 不可变数组
dict  = 键值对表，用 key 查 value
set   = 不重复元素集合
str   = 不可变字符序列
```

最常用的是：

```python
list
dict
str
```

例如：

```python
nums = [1, 2, 3]                    # 列表
person = {"name": "Tom", "age": 18} # 字典
text = "hello"                      # 字符串
```

这三个先掌握，Python 基础数据结构就入门了。