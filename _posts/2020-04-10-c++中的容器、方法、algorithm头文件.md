---
tag: [C++]
category: true
---
* 关联容器map中的count()方法。  
方法返回指定键值的元素数量。

>特别的，可以判定某一键值的元素是否存在

- < algorithm >中的`rotate`  
  其功能等效于如下代码中的功能，即**旋转范围内的元素的顺序[first,last)，以这种方式使由Middle指向的元素成为新的第一个元素。**
```c++
  template <class ForwardIterator>
  void rotate (ForwardIterator first, ForwardIterator middle, ForwardIterator last)
{
  ForwardIterator next = middle;
  while (first!=next)
  {
    swap (*first++,*next++);
    if (next==last) next=middle;
    else if (first==middle) middle=next;
  }
}
```       

 此方法很好的解决了[189.旋转数组](https://leetcode-cn.com/problems/rotate-array/)问题  
 <font color = "red">该方法适用数组元素个数>2的数组</font>

- 关于重载运算符的一些问题    
  1. 当你打算重载像"<<"这样的双目运算符并且该函数有两个参数时应当作为友元函数来重载，否则会出现类似"参数过多"的提示

