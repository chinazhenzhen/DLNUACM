## 概述
| 排列相关  | Implementation function |  
| --------- | --------- |  
|next_permutation|Transform range to next permutation |
|prev_permutation|Transform range to previous permutation|  
全排列是一个经典问题，从 n 个不同元素中任取 m(m ≤ n) 个元素，按
照一定的顺序排列起来，叫做从 n 个不同元素中取出 m 个元素的一个 排
列。当 m = n 时所有的排列情况叫 **全排列**。  

例如排列 1, 2, 3(n = m = 3) 的下一个排列是 1, 3, 2，使
用 ```next_permutation()```可以很便捷地求出下一个排列的结果。  

## 代码  
```
#include <iostream>     // std::cout
#include <algorithm>    // std::next_permutation, std::sort

int main () {
    int myints[] = {1, 2, 3};
    std::sort(myints, myints + 3);
    std::cout << "The 3! possible permutations with 3 elements:\n";
    do {
        std::cout << myints[0] << ' ' << myints[1] << ' ' << myints[2] << '\n';
    } while ( std::next_permutation(myints, myints + 3) );

    std::cout << "After loop: " << myints[0] << ' ' << myints[1] << ' ' << myints[2] << '\n';
    return 0;
}
```  
程序输出结果为：  
```
The 3! possible permutations with 3 elements:
1 2 3
1 3 2
2 1 3
2 3 1
3 1 2
3 2 1
After loop: 1 2 3
```
