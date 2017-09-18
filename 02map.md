## 概述
映射是指两个集合之间的元素的相互对应关系。通俗地说，就是一个元素
对应另外一个元素。比如有一个姓名的集合 {"Tom", "Jone", "Mary"}，班
级集合 {1, 2}。姓名与班级之间可以有如下的映射关系：  
class("Tom") = 1，class("Jone") = 2，class("Mary") = 1  

我们称其中的姓名集合为 关键字集合（key），班级集合为 值集合（value）。  
在 C++ 中我们常用的映射是 map，在 Java 中常用映射是 HashMap。  

**引用库**  
在 C++ 中 map的实现在一个 <map>头文件中，在代码开头引入这个头文
件，并且加上一句 using namespace std。  

```
#include <map>
using namespace std;
```

**构造一个映射**  
现在我们来构造一个映射。
在 C++ 中，我们构造一个 map的语句为： ```map<T1,T2>m```;。这样我们定义了
一个名为 m的从 T1类型到 T2类型的映射。初始的时候 m是空映射。  

**插入映射**  
在 C++ 中通过 ```insert()```方法向集合中插入一个新的映射，参数是一
个 pair类型的结构。这里需要用到另外一个 STL 模板——元组
（ pair）， ```pair<int,char>(1,'a')``` 定义了一个整数 1 和字符 a
的 pair。我们向映射中加入新映射对的时候就是通过加入 pair来实现
的。如果插入的 ```key``` 之前已经有了 ```value```，将会用插入的新的 ```value``` 替
代原来的 ```value```。  
```
#include <map>
#include <string>
using namespace std;
int main() {
    map<string, int> dict;  // {}
    dict.insert(pair<string, int>("Tom", 1)); // {"Tom"->1}
    dict.insert(pair<string, int>("Jone", 2)); // {"Tom"->1, "Jone"->2}
    dict.insert(pair<string, int>("Mary", 1)); // {"Tom"->1, "Jone"->2, "Mary"->1}
    dict.insert(pair<string, int>("Tom", 2)); // {"Tom"->2, "Jone"->2, "Mary"->1}
    return 0;
}```  

**访问映射**  
在 C++ 中访问映射和数组一样，直接用``` []```就能访问。比如``` dict["Tom"]```
就可以获取 ```"Tom"```的班级了。而这里有一个比较神奇的地方，如果没有
对 ```"Tom"```做过映射的话，此时你访问 ```dict["Tom"]```，系统将会自动
为 ```"Tom"```生成一个映射，其 ```value```为 ```key```类型的默认值。并且我们可以之
后再给映射赋予新的值，比如 ```dict["Tom"]=3```，这样为我们提供了另一
种方便的插入手段。当然有些时候，我们不希望系统自动为我们生成映
射，这时候我们需要检测 ```"Tom"```是否已经有映射了，如果已经有映射再继
续访问。这时就需要用``` count()```函数进行判断。  
```
#include <map>
#include <string>
#include <stdio.h>
using namespace std;
int main() {
    map<string, int> dict;  // {}
    dict["Tom"] = 1; // {"Tom"->1}
    dict["Jone"] = 2; // {"Tom"->1, "Jone"->2}
    dict["Mary"] = 1; // {"Tom"->1, "Jone"->2, "Mary"->1}
    printf("Mary is in class %d\n", dict["Mary"]);
    printf("Tom is in class %d\n", dict["Tom"]);
    return 0;
}
```

**查找关键字**  
在 C++ 中，如果你想知道某个关键字是否被映射过，你可以直接
用 ```count()```方法。如果被映射过，返回 1，否则会返回 0。
```
#include <map>
#include <string>
#include <stdio.h>
using namespace std;
int main() {
    map<string, int> dict;  // {}
    dict["Tom"] = 1; // {"Tom"->1}
    dict["Jone"] = 2; // {"Tom"->1, "Jone"->2}
    dict["Mary"] = 1; // {"Tom"->1, "Jone"->2, "Mary"->1}
    if (dict.count("Mary")) {
        printf("Mary is in class %d\n", dict["Mary"]);
    } else {
        printf("Mary has no class");
    }
    return 0;
}
```
**遍历映射**  
在 C++ 中，通过迭代器可以访问映射中的每对映射，每个迭代器
的 ```first```值对应 *key*， ```second```值对应 *value*。  
```
#include <map>
#include <string>
#include <iostream>
using namespace std;
int main() {
    map<string, int> dict;  // {}
    dict["Tom"] = 1; // {"Tom"->1}
    dict["Jone"] = 2; // {"Tom"->1, "Jone"->2}
    dict["Mary"] = 1; // {"Tom"->1, "Jone"->2, "Mary"->1}
    for (map<string, int>::iterator it = dict.begin()； it != dict.end(); ++it) {
        cout << it->first << " is in class " << it->second << endl;
    }
    return 0;
}
```

**清空**  
C++  中都只需要调用``` clear()```方法就可清空。
