## 算法 Algorithm
1. 讲讲你在项目中用到过那些算法   from 阿里PI

图像还原算法 grgb
色彩近似度

2. 1亿的double排序前1000,10000 from 阿里PI

### 

#### 二分查找
#### 分治算法
  移动5层的汉诺塔 从a->c
  public static void main(String[] args){
moveTopTowers(5,'a','b','c')
}
 public static void moveTopTowers(int num,char from,char with,char to){
if(num == 1){
system.out.printLn("第1个盘从" +from+"->"+to)
}else{
 moveTopTowers(num-1,from,to,with)
 system.out.println("第"+num+"个盘从" +from+"->"+to)
moveTopTowers(num-1,with,from,to)
}
}
#### 动态规则算法 
 01背包问题 v[i][j]前i个物品能装入容量为j 的背包的最大价值
1. 制表 推导公式

#### KMP字符串查找算法
BBC  ABCDAB  ABCDABCDABDE
         ABCDABD
暴力匹配优化  
已匹配字符数-对应部分匹配值 
                           ABCDABD
                            0000120  前缀集合和后缀集合 最长的共有元素长度
1. 先得到子串的部分匹配表
2. 使用部分匹配表完成KMP匹配

### 求组合问题(电台覆盖)
#### 贪心算法 
从可以覆盖最多城市的电台开始 加入集合 将覆盖地区从库中移除 
重复上述步骤直到将所有地区覆盖

### 最短路径
#### 迪杰斯拉算法

### 最小生成树 
### 普利姆算法  
 随便从一点开始 找寻最近的点拉入图中  再以图中的点向外找最近的点 重复执行 直到所有的点都加入集合
### 克鲁斯卡尔  
 从最短边开始依次链接  不产生闭环
