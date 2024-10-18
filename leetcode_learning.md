### 1.[13. 罗马数字转整数](https://leetcode.cn/problems/roman-to-integer/)

#### （1）数组若确定没有0值，遍历可直接用是s[i]作为条件

```c
for (; s[i]; i++) { // 遍历相邻的罗马数字
```

#### （2）通过使用哈希表，减少if语句

```c
int roman[128];
roman['I'] = 1;
roman['V'] = 5;
```

---

### 2.[20. 有效的括号](https://leetcode.cn/problems/valid-parentheses/)

#### 可以通过使用函数来减少if语句

```c
char pair(char s) {
    if (s==')') return '(';
    if (s==']') return '[';
    if (s=='}') return '{';
    return 0;
}
```

***

### 3.