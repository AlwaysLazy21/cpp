# C++基础

## 1 基本语法

### 注释

```c++
// 描述信息
/* 描述信息 */
```

> 编译器在编译代码的时候，会忽略注释的内容

### 变量

> 语法：数据类型 变量名 = 初始值

> 局部变量只定义的话，编译器会随机赋值

### 常量

1. #define 宏常量 : #define 常量名

   > #define 本质是内容的替换后，进行编译

2. const 修饰的变量：const 数据类型 常量名 = 常量值

   > const 是变量的引用

### number变量

| short | int  | long | long long | float | double | long double |
| :---: | :--: | :--: | :-------: | :---: | :----: | :---------: |
|   2   |  4   | 4\|8 |     8     |   4   |   8    |     16      |

### 字符型

>  字符型变量用于显示单个字符

>  语法：char ch = 'a'

> 字符使用单引号括起来，且里面只有一个字符
>
> c和c++中的字符型只占用一个字节，字符串在存储的时候是将ASCII编码，放入到存储单元存储，也可以直接赋值ASCII码对应的值

### ASCII码

> 0-31 控制字符，32-127 在键盘上都可以找到

### 转义字符

| 转义字符 | 含义                             | 备注               |
| -------- | -------------------------------- | ------------------ |
| \a       | 换行，将当前位置移动到下一行开头 | 格式化输出         |
| \n       | 水平制表符，跳到下一个TAB位置    | 输出美观           |
| \r       | 回车，将当前位置移动到本行开头   | 可以用来制作进度条 |

### 字符串型

> 作用：用于表示一串字符

> C风格字符串：char 变量名[] = "字符串值";
>
> C++风格字符串：string 变量名 = "字符串值";
>
> 注：c++风格字符串需要加入头文件 #include<string> ，但是 #include<iostream> 隐式包含 std::string

### 布尔类型

> 作用：代表真或假的值

- true --真（本质是1）
- false --假（本质是0）

bool 类型占一个字节 即 sizeof(bool)==1；

### 数据的输入，输出

> 作用：用于从键盘获取数据

> 输入：cin >> 变量 >> 变量 ；
>
> 输出：cout << 变量 << "AlwaysLazy21" << endl;

### 运算符

> 作用：用于执行代码的运算

- 算术运算符

  > 作用：处理四则运算
  >
  > 即 加减乘除，取余，前置递增（递减），后置递增（递减）
  >
  > 注：同类型在经过运算后，结果还是同类型。
  >
  > ​	整型 / 整型 = 商
  >
  > ​	只用整型可以取余
  >
  > ​	前置递增（递减）先对变量进行++（--），再计算表达式，后置相反

- 赋值运算符

  > =, +=, -=, *=, /=, %=
  >
  > 逻辑：左边对右边的结果运算后，再赋值给左边

- 比较运算符

  > ==, !=, <, >, <=, >=
  >
  > 比较后返回 1 或 0

- 逻辑运算符

  > ! 非，&& 与，|| 或

### 程序流程结构

#### 顺序结构

1. if 语句

   ```c++
   if(条件){
       /* code */
   }else if(条件){
       /* code */
   }else if(条件){
       /* code */
   }else{
       /* code */
   }
   ```

2. 三目运算符

   > 语法：表达式1  ? 表达式2 : 表达式3
   >
   > 表达式1的值为真，执行表达式2，否则执行 表达式3

3. switch语句

   ```c++
   switch(表达式){
       case 结果1: 执行语句;break;
       case 结果2: 执行语句;
       case 结果3: 执行语句;break;
       default:执行语句;break;
   }
   ```

   > 结果x 只能是整型或者字符型
   >
   > case 里面如果没有break，那么程序继续往下执行
   >
   > switch 比 if 执行效率高

### 循环结构

1. while 循环语句

   > 满足循环条件，执行循环语句
   >
   > ```c++
   > while(条件){
   >     /* code */
   > }
   > ```

2. do...while循环语句

   > 先执行一次 /* code */ ，再判断条件是否成立

3. for 循环语句

   ```c++
   for(/* 初始表达式 */int i=0;/* 判断条件 */i<n;/* 末尾表达式 */i++){
       /* code */
   }
   ```

### 跳转语句

1. break 语句

   > 跳出 switch 语句、跳出当前最小循环

2. continue 语句

   > 跳过未执行的语句，进行下次循环

3. goto 语句，无条件跳转语句

   ```c++
   int main() {
   cout << "1" << endl;
   goto FLAG;
   cout << "2" << endl;
   cout << "3" << endl;
   cout << "4" << endl;
   FLAG:
   cout << "5" << endl;
   system("pause");
   return 0;
   }
   ```

### 数组

> 相同的数据类型，连续的内存

> 定义：数据类型 数组名[ 数组长度 ];
>
> ​			数据类型 数据名[ 数组长度 ] = {值, 值};
>
> ​			数据类型 数组名[ ] = {值, 值, 值};

#### 数组数组名

> 使用 sizeof(数组名)，统计整个数组在内存中的长度
>
> 获取输组在内存中的首地址

#### 二维数组

```c++
size_t nums[h][r];
size_t nums[h][r]={{val_1,val_2},{val_3,val_4}};
size_t nums[h][r]={val_1,val_2,val_3,val_4};
size_t nums[ ][r]={val_1,val_2,val_3,val_4};
```



### 函数

> 将一段经常使用的代码封装起来，减少重复代码，一个函数实现特定的功能

#### 函数的定义

```c++
返回值类型 函数名 (参数列表)
{
    函数体语句
    return 表达式 
}
```

#### 函数的调用

> 函数名 (参数)
>
> 值传递，地址传递，引用传递

#### 函数的分文件编写

1. 创建后缀名为.h的头文件
2. 创建后缀名为.cpp的源文件
3. 在头文件中写函数的声明
4. 在源文件中写函数的定义

 编译命令

```powershell
g++ -c ./main.cpp ./demo.h ./demo.cpp   // 编译文件
g++ -o 生成的exe名 ./main.o ./demo.o     // 链接文件
```

### 指针的基本概念

> 指针间接访问内存，一般是十六进制

> 定义：size_t * name;
>
> 空指针：size_t *name =NULL; 指针变量指向内存中编号为0的空间，不可访问

#### const 修饰指针

> const size_t* 常量指针
>
> size_t* const 指针常量
>
> const size_t* const name; 常量指针&&指针常量

#### 指针应用

> 1. 利用指针访问数组中的元素
> 2. 利用指针做函数参数，可以修改实参的值

### 结构体

```c++
struct 结构体名{
    结构体成员列表
};
```

> 定义：struct 结构体名{ 结构体成员列表 };
>
> ​		   struct 结构体名={成员1值, 成员2值}
>
> ​		   定义结构体时顺便创建变量

#### 结构体应用

> 结构体数组，结构体指针，结构体做函数参数
>
> 指针 -> 成员属性，变量名 . 成员属性

### 引用

```c++
size_t var_1 = data;
size_t& var_2 = var_1;
```

引用相当于指针常量，不能修改指向

## c++核心编程

### 内存分区

1. 代码区：存放函数的二进制代码，由操作系统进行管理
2. 全局区：存放全局变量和静态变量以及常量
3. 栈区：由编译器自动分配释放，存放函数的参数值，局部变量等
4. 堆区：由程序员分配和释放，若程序员不是放，程序结束时由操作系统回收

#### 注

堆区的使用

```c++
auto p=new size_t();
auto p=new siz
```



## c++提高编程

### 模板









### STL

#### 六大组件

容器、算法、迭代器、仿函数、适配器、空间配置器

#### 容器

| 泛型类                     | 中文     |
| -------------------------- | -------- |
| vector                     | 数组     |
| string                     | 字符串   |
| set/multiset/unordered_set | 集合     |
| map/unordered_map/multimap | 图       |
| list                       | 链表     |
| deque                      | 双端队列 |
| queue                      | 队列     |
| stack                      | 栈       |
| pair                       | 对       |

### string

```c++
//构造函数
string();	//构建一个空的字符串 例如：string str;
string(const char* s);	//使用字符串s初始化
string(const string& str);	//使用一个string对象初始化另一个string对象
string(int n,char c);	//使用n个字符c初始化
//赋值函数
string& operator=(const char* s);	//char*类型字符串，赋值给当前字符串
string& operator=(const string &s);	//把字符串s赋值给当前的字符串
string& operator=(char c);	//字符赋值给当前字符串
string& assign(const char *s);	//把字符串s赋值给当前字符串
string& assign(const char *s,int n);	//把字符串s的前n个字符付给当前字符串
string& assign(const string &s);	//把字符串s赋值给当前字符串
string& assign(int n,char c);	//用n个字符c赋值给当前字符串
//拼接操作
string& operator+=(const char* str);	//重载+=操作符
string& operator+=(const char c);	//重载+=操作符
string& operator+=(const string& str);	//重载+=操作符
string& append(const char *s);	//把字符串s连接到当前字符串结尾
```





#### stack

```c++
//构造函数
stack<T> stk;	//stack采用模板类实现，stack对象的默认构造形式
stack<const stack &stk>;	//拷贝构造函数
stack& operator=(const stack &stk);	//重载等号操作符
push(elem);	//向栈顶移除第一个元素
pop();	//删除栈顶元素
top();	//返回栈顶元素
empty();	//判断堆栈是否为空
size();	//返回的栈的大小
```

#### map

```c++
//构造函数
map<T1,T2> mp;	//默认构造函数
map(const map &mp);	//拷贝构造函数
map& operator=(const map &mp);	//重载构造函数
size();	//返回容器中元素的数目
empty();	//判断容器是否为空
swap(st);	//交换两个集合容器
insert(elem);	//在容器中插入元素
clear();	//清除所有元素
earse(pos)	//删除pos迭代器所指的元素，返回下个元素的迭代器
earse(begin,end);	//删除区间[begin,end)的所有元素返回写个元素的迭代器
earse(key);	//删除容器中值为key的元素
find(key);	//查找key是否存在，若存在，返回该键的元素的迭代器，若不存在，返回set.end();
count(key);	//统计key的元素个数

```

