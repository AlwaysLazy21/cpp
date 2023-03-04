# c++ 提高编程

## 模板

### 模板

概念：建立通用的模具，大大提高复用性

### 函数模板

c++另一种编程思想：泛型编程

c++提供两种模板机制：函数模板 和 类模板

#### 函数模板语法

```c++
template<typename T>
void* function(T a,T b);
函数声明或定义
// template 声明创建模板
// typename 表明其后面的符号是一种数据类型，可以用class代替
// T 通用的数据类型，名称可以替换，通常为大写字母
function(10,100);	// 自动推导类型
function<int>(100,2);	// 显式指定类型
```

#### 类模板与函数模板的区别

1. 类模板没有自动类型推导的使用方式，必须使用显式推导类型
2. 类模板在模板参数列表中可以有默认参数

```c++
template<class T,class Y=int>
```

类模板更倾向于明示类的类型

## 容器

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
string& append(const char *s,int n);	// 把字符串s的前n个字符连接到当前字符串结尾
string& append(const string &s);	// 同operator+=(const string& str)
string& append(const string &s,int pos,int n);	//字符串s中从pos开始的n个字符连接到字符串结尾
//查找函数
int find(const string& str,int pos=0)const;	//查找str第一次出现的位置，从pos开始查找
int find(const char* s,int pos=0)const;	//查找s第一次出现的位置，从pos开始查找
int find(const char* s,int pos,int n)const;	//从pos位置查找s的前n个字符第一次位置
int find(const char c,int pos=0)const;	//查找字符c第一次出现位置
int rfind(const string& str,int pos=npos)const;	//查找str出现的最后一次位置，从pos开始查找
int rfind(const char* s,int pos=npos)const;	//查找s最后一次出现位置，从pos开始查找
int rfind(const char* s,int pos,int n)const;	//从pos查找s的前n个字符最后一次位置
int rifnd(const char c,int pos=0)const;	//查找字符c最后一次出现位置
string& replace(int pos,int n,const string& str);	//替换从pos开始n个字符为字符串str
string& replace(int pos,int n,const char* s);	//替换从pos开始的n和字符为字符串s
int conpare(const string &s)const;	//与字符串s比较
int compare(const char* s)const;	//与字符串s比较
char& operator[](int n);	//通过[]方式取字符
char& at(int n);	//通过at方法获取字符
string& insert(int pos,const char*s);	//插入字符串
string& insert(int pos,const string &s);	//插入字符串
string& insert(int pos,int n,char c);	//在指定位置插入n个字符c
string& erase(int pos,int n=npos);	//删除从pos开始的n个字符
string substr(int pos=0,int n=npos)const;	//返回由pos开始的n个字符串组成的字符串
```

### vector

```c++
vector<T> v;	//采用模板实现类实现，默认构造函数
vector(v.begin(),v.end());	//将v[being(),end()]区间中的元素拷贝给本身
vector(n,elem);	//构造函数将n个elem拷贝给本身
vector(const vector &vec);	//拷贝构造函数
vector& operator=(const vector &vec);	//重载等号操作符
assign(beg,end);	//将[beg,end]区间中的数据拷贝赋值给本身
assign(n,elem);	//将n个elem拷贝赋值给本身
empty();	//判断容器是否为空
capacity();	//容器的容量
size();	//返回容器中元素的个数
resize(int num);	//重新指定容器的长度为num，若容器变长，则以默认值填充新位置；若容器变短，则末尾超出容器长度的元素被删除
push_back(ele);	//尾部插入元素ele
pop_bacK();//删除最后一个元素
insert(const_inerator pos,ele);	//迭代器指向位置pos插入元素ele
insert(const_inerator pos,int count,ele);	//迭代器指向位置pos插入count个元素ele
erase(const_iterator pos);	//删除迭代器指向的元素
erase(const_iterator start,const_iterator end);	//删除迭代器从start到end之间的元素
clear();	//删除元素中的所有元素
at(int index);	//返回索引index所指的元素
operator[](int index);	//返回索引index所指的数据
front();	//返回容器中第一个数据元素
back();	//返回容器中最后一个数据元素
swap(vec);	//将vec与本身的元素互换
reverse(int len);	//容器预留len个元素长度，预留位置不初始化，元素不可访问
```

### deque

双端数组，可以对头部进行插入删除操作

vector 对于头部的插入效率低，数据量越大，效率越低

deque 相对而言，对头部的插入删除的速度比vector快

vector 访问元素时的速度会比deque快，这和两者的内部实现有关

```c++
deque<T> deqT;	//默认构造形式
deque(begin,end);	//构造函数将[begin,end)区间的元素拷贝给本身
deque(n,ele);	//将n个ele拷贝给本身
deque(const deque &deq);	//拷贝构造函数
deque& operator=(const deque &deq);	//重载等号操作符
assign(begin,end);	//将[begin,end)区间中的数据拷贝赋值给本身
assign(n,ele);	//将n个ele拷贝赋值给本身
empty();	//判断容器是否为空
size();	//返回容器中元素的个数
resize(num);	//重新指定容器的长度为num，若容器变长，则以默认值填充新位置，若容器变短，末尾超出容器长度的元素被删除
resize(num,ele);	//重新指定容器的长度为num，若容器变长，则以ele填充新位置，若容器变短，末尾超出容器长度的元素被删除
push_back(ele);	//在容器的末尾添加一个数据
push_front(ele);	//在容器头部插入一个数据
pop_back();	//删除容器的最后一个元素
pop_front();	//删除容器的第一个元素
insert(pos,ele);	//在pos位置插入n个ele数据，无返回值
insert(pos,begin,end);	//在pos位置插入[beign,end)区间的数据，无返回值
clear();	//清空容器中的所有数据
erase(begin,end);	//删除[begin,end)区间的数据，返回下一个数据的位置
erase(pos);	//删除pos位置的数据，返回下个位置的数据
at(int index);	//返回索引index所指的数据
operator[](int index);	//返回索引index所指的数据
front();	//返回容器中的第一个数据元素
back();	//返回容器中最后一个数据元素
```

### stack

```c++
stack<T> stk;	//采用模板类实现，默认构造
stack(const stack &stk);	//拷贝构造函数
stack& operator=(const stack &stk);	//重载等号操作符
push(ele);	//向栈顶添加元素
pop(ele);	//删除栈顶元素
top();	//返回栈顶元素
empty();	//判断堆栈是否为空
size();	//返回栈的元素个数

```

### queue

队列容器从一端新增元素，从另一端删除元素

```c++
queue<T> que;	//queue采用模板类实现，queue对象的默认构造函数
queue(const queue &que);	//拷贝构造函数
queue& operator=(const queue &que);	//重载等号操作符
push(ele);	//往容器尾添加元素
pop();	//删除容器的第一个元素
back();	//返回最后一个元素
front();	//返回第一个元素
back();	//返回最后一个元素
empty();	//判断容器是否为空
size();	//返回容器中元素的个数
```

### list

将数据进行链式存储，链表是一种物理存储单元上非连续的存储结构，数据元素的逻辑顺序是通过链表中的指针链接实现的链表的组成，链表由一系列的结点组成

结点的组成：一个是存储数据单元的数据域，另一个是存储下一个结点地址的指针域

STL中的链表是一个双向循环列表

```c++
list<T> l;	//list采用模板类实现，默认构造
list(begin,end);	//将[begin,end)区间中的元素拷贝给本身
list(n,ele);	//将n个ele拷贝给本身
list(const list &l);	//拷贝构造函数
assign(begin,end);	//将[begin,end)区间中的数据拷贝赋值给本身
assing(n,ele);	//将n个ele拷贝构造给本身
list& operator=(const list &l);	//重载等号操作符
swap(l);	//将l与本身的元素进行互换
size();	//返回容器中元素的个数
empty();	//判断容器是否为空
resize();	//重新指定容器的长度为num，若容器变长，则以默认值填充新位置；若容器变短，则末尾超出容器的长度的元素被删除。
resize(num,ele);	//重新指定容器的长度为num，若容器变长，则以ele填充新位置；若容器变短，则末尾超出容器长度的元素被删除
push_back(ele);	//将ele添加到容器的末尾
pop_back();	//删除容器的最后一个元素
push_front(ele);	//将ele插入待容器的开头
pop_front();	//移除容器开头的第一个元素
insert(pos,ele);	//在pos位置插入ele元素的拷贝，返回新数据的位置
insert(pos,n,ele);	//在pos位置插入n个ele元素，无返回值
insert(pos,begin,end);	//在pos位置插入[begin,end)区间的数据，无返回值
clear();	//移除容器的所有数据
erase(begin,end);	//删除[begin,end)区间的数据，无返回值
clear(pos);	//删除pos位置的数据，返回下个数据的位置
remove(ele);	//删除容器中所有与ele值匹配的元素
front();	//返回第一个元素
back();	//返回最后一个元素
reverse();	//反转链表
sort();	//链表排序
```

### set

```c++
set<T> s;	//默认构造函数
set(const set& s);	//拷贝构造函数
set& operator=(const set &s);	//重载等号操作符
size();	//返回容器中的元素个数
empty();	//判断容器是否为空
swap(s);	//交换两个集合容器
insert(ele);	//将ele插入容器中
clear();	//清除所有元素
erase(pos);	//删除pos迭代器所指的元素，返会下一个元素的迭代器
erase(begin,end);	//删除区间[begin,end)区间内的所有元素，返回下一个元素的迭代器
erase(ele);	//删除容器中值ele的元素
find(key);	//查找key是否存在，返回该件的元素的迭代器，若不存在，返回set.end();
count(key);	//统计key的元素个数
```

### multiset

set和multiset的区别

set不可以插入重复数据，而multiset可以

set插入数据的同时返回插入结果，表示插入是否成功

multiset不会检测数据，因此可以插入重复数据

### unordered_set

set与unordered_set的区别：

不对插入集合内的数据进行排序



### algorithm

```c++
sort(iterator begin,iterator end);	//对[begin,end)区间内的元素进行排序
```

