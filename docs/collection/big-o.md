## 时间复杂度

“二哥，为什么要讲时间复杂度呀？”三妹问。

“因为接下来要用到啊。后面我们学习 ArrayList、LinkedList 的时候，会比较两者在增删改查时的执行效率，而时间复杂度是衡量执行效率的一个重要标准。”我说。

“到时候跑一下代码，统计一下前后的时间差不更准确吗？”三妹反问道。

“实际上，你说的是另外一种评估方法，这种评估方法可以得出非常准确的数值，但也有很大的局限性。”我不急不慢地说。

第一，测试结果会受到测试环境的影响。你比如说，同样的代码，在我这台 iMac 上跑出来的时间和在你那台华为的 MacBook 上抛出的时间可能就差别很大。

第二，测试结果会受到测试数据的影响。你比如说，一个排序后的数组和一个没有排序后的数组，调用了同一个查询方法，得出来的结果可能会差别特别大。

“因此，我们需要这种不依赖于具体测试环境和测试数据就能粗略地估算出执行效率的方法，时间复杂度就是其中的一种，还有一种是空间复杂度。”我继续补充道。

来看下面这段代码：

```java
public static int sum(int n) {
    int sum = 0; // 第 1 行
    for (int i=0;i<n;i++) { // 第 2 行
        sum = sum + 1; // 第 3 行
    } // 第 4 行
    return sum; // 第 5 行
}
```

这段代码非常简单，方法体里总共 5 行代码，包括“}”那一行。每段代码的执行时间可能都不大一样，但假设我们认为每行代码的执行时间是一样的，比如说 unit_time，那么这段代码总的执行时间为多少呢？

“这个我知道呀！”三妹喊道，“第 1、5 行需要 2 个 unit_time，第 2、3 行需要 2*n*unit_time，总的时间就是 2(n+1)*unit_time。”

“对，一段代码的执行时间 T(n) 和总的执行次数成正比，也就是说，代码执行的次数越多，花费的时间就越多。”我总结道，“这个规律可以用一个公式来表达：”

> T(n) = O(f(n))

f(n) 表示代码总的执行次数，大写 O 表示代码的执行时间 T(n) 和 f(n) 成正比。

这也就是大 O 表示法，它不关心代码具体的执行时间是多少，它关心的是代码执行时间的变化趋势，这也就是时间复杂度这个概念的由来。

对于上面那段代码 `sum()` 来说，影响时间复杂度的主要是第 2 行代码，其余的，像系数 2、常数 2 都是可以忽略不计的，我们只关心影响最大的那个，所以时间复杂度就表示为 `O(n)`。

常见的时间复杂度有这么 3 个：

1）`O(1)`

代码的执行时间，和数据规模 n 没有多大关系。

括号中的 1 可以是 3，可以是 5，可以 100，我们习惯用 1 来表示，表示这段代码的执行时间是一个常数级别。比如说下面这段代码：

```java
int i = 0;
int j = 0;
int k = i + j;
```

实际上执行了 3 次，但我们也认为这段代码的时间复杂度为 `O(1)`。

2）`O(n)`

时间复杂度和数据规模 n 是线性关系。换句话说，数据规模增大 K 倍，代码执行的时间就大致增加 K 倍。

3）`O(logn)`

时间复杂度和数据规模 n 是对数关系。换句话说，数据规模大幅增加时，代码执行的时间只有少量增加。

来看一下代码示例，

```java
public static void logn(int n) { 
    int i = 1;
    while (i < n) {
        i *= 2;
    }
}
```

换句话说，当数据量 n 从 2 增加到 2^64 时，代码执行的时间只增加 64 倍。

```
遍历次数 |   i
----------+-------
    0     |   i
    1     |  i*2
    2     |  i*4
   ...    |  ...
   ...    |  ...
    k     |  i*2^k 
```

“好了，三妹，这节就讲到这吧，理解了上面 3 个时间复杂度，后面我们学习 ArrayList、LinkedList 的时候，两者在增删改查时的执行效率就很容易对比清楚了。”我抬起头看了看三妹说，她似乎有些明白，又有些不太明白。

“不要担心哥，我再温习一遍就能搞懂了。”三妹很乖。

----------


《**Java 程序员进阶之路**》预计一个月左右会有一次内容更新和完善，大家在我的公众号 **沉默王二** 后台回复“**03**” 即可获取最新版！如果觉得内容不错的话，欢迎转发分享！

<img src="https://cdn.jsdelivr.net/gh/itwanger/toBeBetterJavaer/images/itwanger.png" alt="图片没显示的话，可以微信搜索「沉默王二」关注" style="zoom:50%;" />