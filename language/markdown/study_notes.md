
https://www.jianshu.com/p/8c1b2b39deb0

{#index}
This is an H1
=============

This is an H2
-------------

# 这是 H1

## 这是 H2

###### 这是 H6

# 这是 H1 #

## 这是 H2 ##

### 这是 H3 ######


区块引用 Blockquotes
> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
> consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
> Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
>
> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
> id sem consectetuer libero luctus adipiscing.
Markdown 也允许你偷懒只在整个段落的第一行最前面加上 > ：
> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
id sem consectetuer libero luctus adipiscing.

区块引用可以嵌套（例如：引用内的引用），只要根据层次加上不同数量的 > ：
> This is the first level of quoting.
>
> > This is nested blockquote.
>
> Back to the first level.

引用的区块内也可以使用其他的 Markdown 语法，包括标题、列表、代码区块等：

> ## 这是一个标题。
>
> 1.   这是第一行列表项。
> 2.   这是第二行列表项。
>
> 给出一些例子代码：
>
>     return shell_exec("echo $input | $markdown_script");

Markdown 支持有序列表和无序列表。

无序列表使用星号、加号或是减号作为列表标记：

*   Red
*   Green
*   Blue

+   Red
+   Green
+   Blue

-   Red
-   Green
-   Blue
有序列表则使用数字接着一个英文句点：
列表项目标记通常是放在最左边，但是其实也可以缩进，最多 3 个空格，项目标记后面则一定要接着至少一个空格或制表符。
1.  Bird
2.  McHale
3.  Parish
如果你的列表标记写成：
1.  Bird
1.  McHale
1.  Parish

或甚至是：

3. Bird
1. McHale
8. Parish

*   Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
    Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
    viverra nec, fringilla in, laoreet vitae, risus.
*   Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
    Suspendisse id sem consectetuer libero luctus adipiscing.

# index



## 链接
1. 链接本地仓库
[我的简介](/example/profile.md)
2. 跳转到[目录](#index)
3. []()
## 数学公式
$$ \sum_{i=1}^n a_i=0$$

$$ f(x_1,x_x,\ldots,x_n) = x_1^2 + x_2^2 + \cdots + x_n^2 $$

$$ \sum^{j-1}_{k=0}{\widehat{\gamma}_{kj} z_k}$$
## 制表符?
产品|价格

姓名 | 技能 | 排行
----|:----:|----
刘备|哭|大哥
关羽|打|二哥
张飞|骂|三弟