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

### 3.[2606. 找到最大开销的子字符串](https://leetcode.cn/problems/find-the-substring-with-maximum-cost/)

#### (1)`ord()`可获取ASCLL码，`chr()`相反

#### (2)`zip()`可以将对象打包成元组

```py
a = [1, 2, 3, 4, 5]
b = [6, 7, 8, 9, 10]
cc = list(zip(a,b))
print(cc)
a1, b1 = zip(*cc)
print(list(a1))
print(list(b1))
```

```py
[(1, 6), (2, 7), (3, 8), (4, 9), (5, 10)]
[1, 2, 3, 4, 5]
[6, 7, 8, 9, 10]
```

若`cc=zip(a, b)`，则会生成一个迭代器，`cc`被使用一次后将被消耗，比如打印之后，`cc`将消失，再对cc进行操作会报错

所以使用在首次创建时，将其转化成列表`cc=list(zip(a,b))`，后续`cc`不会消失，也就可以对`cc`进行多次操作，比如打印、解包

#### (3)[dict.get(key, default=None)](https://www.runoob.com/python3/python3-att-dictionary-get.html)返回指定键的值，如果键不在字典中返回 default 设置的默认值

```py
a = "abcdef"
b = "123456"
c = dict(zip(a,b))
print(c)
print(c.get('a',ord('a')),c.get('z',ord('z')))
```

```py
{'a': '1', 'b': '2', 'c': '3', 'd': '4', 'e': '5', 'f': '6'}
1 122
```

***

### 4.[2466. 统计构造好字符串的方案数](https://leetcode.cn/problems/count-ways-to-build-good-strings/)

#### (1)最大公约数（GCD）某些时候可以减小问题规模

```python
g = gcd(zero, one)
```

***

### 5.[209. 长度最小的子数组](https://leetcode.cn/problems/minimum-size-subarray-sum/)

求总和大于等于 `target` 的长度最小的子数组时，每次计算出前缀和判断是否大于`target`都会从前往后减去数组里的值，可以优化每次不用重复减，上次减完不用还原，减少重复的删除过程,也就是滑动窗口

```C++
int minSubArrayLen(int target, vector<int>& nums) {
        int n = nums.size();
        int ans = n+1,l = 0,s = 0;
        for(int i = 0; i<nums.size();i++){
            s+=nums[i];
            while(s>=target){
                ans = min(ans,i-l+1);
                s -= nums[l++];
            }
        }
        return ans<=n ? ans:0;
    }
```

### 6.[2904. 最短且字典序最小的美丽子字符串](https://leetcode.cn/problems/shortest-and-lexicographically-smallest-beautiful-string/)

C++计数：

```C++
count(s.begin(),s.end(),'1') // 统计字符 1 的个数
```

获取子串：第一个参数为起始位置，第二个参数为长度

```C++
s.substr(l,r-l+1);
```

### 7.[1574. 删除最短的子数组使剩余数组有序](https://leetcode.cn/problems/shortest-subarray-to-be-removed-to-make-array-sorted/)

注意与或运算先后顺序

```
while(r<n && arr[l]>arr[r] )r++; //先判断 r<n 再判断 arr[l]>arr[r]
```

若写成arr[l]>arr[r] && r<n，则会先判断arr[l]>arr[r]，最后由于r++超出数组索引报错

### 8.[3011. 判断一个数组是否可以变为有序](https://leetcode.cn/problems/find-if-array-can-be-sorted/)

`‌__builtin_popcount()`**函数用于计算一个整数的二进制表示中1的个数‌**
