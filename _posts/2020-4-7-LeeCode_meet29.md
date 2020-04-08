# LeeCode算法题库

## 29.顺时针打印矩阵

### 题干


> 输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字。

### 算法演示


先贴一下代码

```java
class Solution {
    public int[] spiralOrder(int[][] matrix) {
        if(matrix.length == 0) return new int[0];
        //二元数组 获取数组长度
        //获取行数 int rowlength = array.length
        //获取列数 int collength = array[0].length
        int  t = 0 , b = matrix.length-1, l = 0, r = matrix[0].length-1; 
        int  x = 0;
        int[]  res= new int[(r+1)*(b+1)];  //定义一个存放编列结果的数组
        while(true){
            //x++ = x   执行计算后 x自加
            //数组非空 先从左到右遍历
            for(int i = l ; i <= r; i++)  res[x++] = matrix[t][i];  // left to right
            if(++t > b) break;  //  先比较 top 与 blow的距离 top 边界缩小         
            for(int i = t; i <= b; i++) res[x++] = matrix[i][r];    //top to blow   
            if(--r< l)  break;
            for(int i = r; i >=l; i--)   res[x++] = matrix[b][i];   //right to left
            if(t > --b)    break;
            for(int i = b; i >= t; i--) res[x++] = matrix[i][l];    //blow to top
            if(++l > r)   break;
        }
        return res;
    }
}
```

### 相关方法

- 二元数组获取长度的方法

  - 获取行数	

  ```java
  int rowlength = array.length;
  ```

  - 获取列数

  ```java
  int collength = array[0].length;
  ```

- x++ 与 ++x 的区别

  x++ ：先用x的原值，计算完成后 x 加 1；

  ++x ： 先给 x 加 1，用 x + 1 的值

  >  口诀 ： ++在前，用新值，先自加；
  >
  > ​		 	 ++在后，用原值，后自加。

### 算法思路

​	根据题意由顺时针输出，设置top 、blow、left、right边界，按照输出的特点，通过循环将矩阵中的元素保存在新数组中，每一轮边界边界缩小，判断边界是否越界

### tip：

- ++x 和 x++ 的操作在这次的题中十分重要