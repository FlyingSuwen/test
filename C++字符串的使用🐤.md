[TOC]

 

# C++字符串的使用🐤

## 输入

==cin==到空格就会截止,若想完全获取则用==getline==

```c++
#include<bits/stdc++.h>
using namespace std;
int main(){
   string wish;
   getline(cin, wish);//后面是数组名,到回车键结束
   cout<<"my wish is "<<wish<<endl;
   return 0;
}
```

## ==定义字符串==

```c++
    string s1;    // 初始化一个空字符串
    string s2 = s1;   // 初始化s2，并用s1初始化
    string s3(s2);    // 作用同上
    string s4 = "hello world";   // 用 "hello world" 初始化 s4，除了最后的空字符外其他都拷贝到s4中
    string s5("hello world");    // 作用同上
    string s6(6,'a');  // 初始化s6为：aaaaaa
    string s7(s6, 3);  // s7 是从 s6 的下标 3 开始的字符拷贝
    string s8(s6, pos, len);  // s7 是从 s6 的下标 pos 开始的 len 个字符的拷贝
```



## 字符串拼接

```c++
str1 = "hel";
str2 = "lo";
str3 = str1 + str2;//输出为hello
str[0] 为 h
```

## find()

```c++
寻找字串
#include <iostream>
#include <string>
using namespace std;

int main() {
    string text = "Hello, World!";
    string word = "World";

    size_t position = text.find(word);//返回第一个字符的的编号
    //int num = text.find(word),如果找到返回的是字符编号,否则-1
    if (position != string::npos) {//npos表示没找到
        cout << "Found '" << word << "' at position: " << position << endl;
    } else {
        cout << "Word not found." << endl;
    }

    return 0;
}
```

```c++
//从指定位置开始寻找
#include <iostream>
#include <string>
using namespace std;

int main() {
    string text = "This is a test. This is only a test.";
    string word = "test";

    size_t position = 0;
    //从position为0的时候开始找
    //也可表示为find("text", position)(具体内容时不可以省略引号)
    while ((position = text.find(word, position)) != string::npos) {
        cout << "Found '" << word << "' at position: " << position << endl;
        position += word.length(); // 移动到子串之后的位置，继续查找
    }

    return 0;
}
```

## rfind()

查找字符串中最后一次出现字串的位置

## 搜索升级

```
s.find_first_of(args)  // 在 s 中查找 args 中任何一个字符最早出现的位置
s.find_last_of(args)  // 在 s 中查找 args 中任何一个字符最晚出现的位置
例如：
string s1 = "nice to meet you~"; 
cout << s1.find_first_of("mey") << endl; // 输出结果为 3，'e' 出现的最早
 
```

```
s.find_first_not_of(args)  // 查找 s 中 第一个不在 args 中的字符的位置
s.find_last_not_of(args)  // 查找 s 中 最后一个不在 args 中的字符的位置
例如：
string s1 = "nice to meet you~";  
cout << s1.find_first_not_of("nop") << endl; // 输出结果为 1 ，'i' 不在 "nop" 里
```



## 判断字符类型

```c++
isalnum(c)  // 当是字母或数字时为真
isalpha(c)  // 当是字母时为真
isdigit(c)  // 当是数字是为真
islower(c)  // 当是小写字母时为真
isupper(c)  // 当是大写字母时为真
isspace(c)  // 当是空白（空格、回车、换行、制表符等）时为真
isxdigit(c) // 当是16进制数字是为真
ispunct(c)  // 当是标点符号时为真（即c不是 控制字符、数字、字母、可打印空白 中的一种）
isprint(c)  // 当是可打印字符时为真（即c是空格或具有可见形式）
isgraph(c)  // 当不是空格但可打印时为真
iscntrl(c)  // 当是控制字符时为真
tolower(c)  // 若c是大写字母，转换为小写输出，否则原样输出
toupper(c)  // 类似上面的
```

## 修改string

```c++
s.insert(pos, args)  
// 在 s 的位置 0 之前插入 s2 的拷贝
s.insert(0, s2)  
```

> 删除从 pos 开始的 len 个字符。如果 len 省略，则删除 pos 开始的后面所有字符。返回一个指向 s 的引用。

```
s.erase(pos, len)  
```

> 将 s 中的[字符替换](https://so.csdn.net/so/search?q=字符替换&spm=1001.2101.3001.7020)为 args 指定的字符。返回一个指向 s 的引用。

```
s.assign(args)  
```

> 将 args 追加到 s 。返回一个指向 s 的引用。args 不能是单引号字符，若是单个字符则必须用双引号表示。如，可以是 s.append(**"**A**"**) 但不能是 s.append(**'**A**'**)   

```
s.append(args)  
```

> 将 s 中范围为 range 内的字符替换为 args 指定的字符。range 或者是一个下标或长度，或者是一对指向 s 的迭代器。返回一个指向 s 的引用。

```
s.replace(range, args) 
// 从位置 3 开始，删除 6 个字符，并插入 "aaa".删除插入的字符数量不必相等
s.replace(3, 6, "aaa")  
```

## 反转字符串

```
    string s2 = "12345";    // 初始化一个字符串
    reverse(s2.begin(), s2.end()); // 反转 string 定义的字符串 s2 
    cout << s2 << endl; // 输出 54321
```

## 提取字符串

使用 **string ss = s.substr(pos, n)** 。从索引 pos 开始，提取连续的 n 个字符，包括 pos 位置的字符。

## string.char.数值类型之间的转换

### 1.数值转为string,数值可以是任何类型

```
string s = to_string(val)
```

### 2.转换为整数并返回

返回类型分别是 int、long、unsigned long、long long、unsigned long long。b 表示转换所用的进制数，默认为10，即将字符串当作几进制的数转换，最终结果仍然是十进制的表示形式 。p 是 size_t  指针，用来保存 s 中第一个非数值字符的下标，默认为0，即函数不保存下标，该参数也可以是空指针，在这种情况下不使用。

**索引信息的作用**----剩余字符串是从哪里开始的

将剩余字符串的起始位置存储到 `pos` 中

如果你不需要索引信息，可以用 `nullptr` 表示“我不需要这个指针指向任何东西

```c++
stoi(s)
// 函数原型 int stoi (const string&  str, size_t* idx = 0, int base = 10);
stoi(s, p, b)//int
stol(s, p, b)//long
stoul(s, p, b)//unsigned long
stoll(s, p, b)//long long
stoull(s, p, b)//unsinged long long
// 例如
string s1 = "11";    // 初始化一个空字符串
int a1 = stoi(s1);
cout << a1 << endl; // 输出 11
int a2 = stoi(s1, nullptr, 8);
cout << a2 << endl; // 输出 9
int a3 = stoi(s1, nullptr, 2);
cout << a3 << endl; // 输出 3
int num = stoi("123abc", nullptr);  // 不关心剩余字符串的索引
size_t pos;
int num = stoi("123abc", &pos);  // pos 的值将是 3
```

### 3.转换为浮点数并返回

返回类型分别是 float、double、long double 。**p** 是 size_t 指针，用来保存 s 中第一个非数值字符的下标，默认为0，即函数不保存下标，该参数也可以是空指针，在这种情况下不使用。

```
stof(s)
stof(s, p)
stod(s, p)
stold(s, p)
```

### 4.char型转数值

注意传入的参数是指针类型，即要对字符取地址

```
atoi(c)
// 函数原型 int atoi(const char *_Str)
atol(c)
atoll(c)
atof(c)
```

```c++
#include <iostream>
#include <cstdlib>  // 包含 atoi 函数的头文件
using namespace std;

int main() {
    const char* str = "12345";
    int num = atoi(str);
    cout << "Converted integer: " << num << endl;

    // 注意：如果字符串中包含非数字字符，转换会停止
    const char* str2 = "123abc";
    int num2 = atoi(str2);
    cout << "Converted integer: " << num2 << endl;

    return 0;
}
```

```
输出:
Converted integer: 12345
Converted integer: 123
```

