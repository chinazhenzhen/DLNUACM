## 概述   
集合是数学中的一个基本概念，通俗地理解，集合是由一些不重复的数据组
成的。比如 {1, 2, 3} 就是一个有 1, 2, 3 三个元素的集合。C++
标准库中的集合支持高效的插入、删除和查询操作，这 3 个操作的时间复
杂度都是 ***O(lg n)***，其中 n 是当前集合中元素的个数。如果用数组，虽然插入的时间复杂度是 ***O(1)***，但是删除和查询都是 ***O(n)***，时间效率太低。
在 C++ 中我们常用的集合是 ```set```。

## 用法   
#### 引用库  
C++ 中 ```set```的实现在一个 ```<set>```头文件中，在代码开头引入这个头文件，并
且同样加上一句 ```using namespace std```。  
```
#include <set>
using namespace std;
```  
#### 构造一个集合  
现在我们来构造一个集合。  
C++ 中直接构造一个 ```set```的语句为： ```set<T>s```。这样我们定义了一个名为 ```s```
的、储存 ```T```类型数据的集合，其中 ```T```是集合要储存的数据类型。初始的时
候 ```s```是空集合。  
#### 插入元素  
C++ 中用 ```insert()```方法向集合中插入一个新的元素。注意**如果集合中已
经存在了某个元素，再次插入不会产生任何效果，集合中是不会出现重复
元素的。**  
```
#include <set>
#include <string>
using namespace std;
int main() {
    set<string> country;  // {}
    country.insert("China"); // {"China"}
    country.insert("America"); // {"China", "America"}
    country.insert("France"); // {"China", "America", "France"}
    return 0;
}
```  
#### 删除元素  
C++ 中通过 ```erase()```方法删除集合中的一个元素，如果集合中不存在这个元素，不进行任何操作。  
```
#include <set>
#include <string>
using namespace std;
int main() {
    set<string> country;  // {}
    country.insert("China"); // {"China"}
    country.insert("America"); // {"China", "America"}
    country.insert("France"); // {"China", "America", "France"}
    country.erase("America"); // {"China", "France"}
    country.erase("England"); // {"China", "France"}
    return 0;
}
```  
#### 查找元素  
C++ 中如果你想知道某个元素是否在集合中出现，你可以直接用 ```count()```
方法。如果集合中存在我们要查找的元素，返回 1，否则会返回 0。  
```
#include <set>
#include <string>
#include <stdio.h>
using namespace std;
int main() {
    set<string> country;  // {}
    country.insert("China"); // {"China"}
    country.insert("America"); // {"China", "America"}
    country.insert("France"); // {"China", "America", "France"}
    if (country.count("China")) {
        printf("China belong to country");
    }
    return 0;
}
```  
#### 遍历元素  
C++ 通过迭代器可以访问集合中的每个元素，迭代器就好比指向集合中
的元素的指针。如果你不了解迭代器，你只需要先记住用法。   
```
#include <set>
#include <string>
#include <iostream>
using namespace std;
int main() {
    set<string> country;  // {}
    country.insert("China"); // {"China"}
    country.insert("America"); // {"China", "America"}
    country.insert("France"); // {"China", "America", "France"}
    for (set<string>::iterator it = country.begin(); it != country.end(); ++it) {
        cout << (*it) << endl;
    }
    return 0;
}
```   
注意，在 C++ 中遍历 ```set```是从小到大进行的。   
#### 清空   
使用```clear()```的方法就可以清空。




## C++ set方法总结  

| 方法 | 功能      |  
| ---- | ------------------------------------- |  
|insert  |插入一个元素 |  
|erase  | 删除一个元素 |  
| count | 判断元素是否在```set```中  |  
| size | 获取元素个数  |  
| clear | 清空  |    

C++ set官方文档（待插入）  
