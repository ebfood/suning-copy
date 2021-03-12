# common.less

媒体查询都在这里, 苏宁写的非常全, 这里用less实现, 把份数设置成变量, 方便改.

```less
@no: 15; //划分15分

@media screen and (min-width: 720px) {
  html {
    font-size: (720px / @no);
  }
}

@media screen and (min-width: 750px) {
  html {
    font-size: (750px / @no);
  }
}


// ... ...
```

**这里一定要从小到大然后用minwidth, 不然会出错**

然后在index.less中导入@import "common";

# index.less

## 准备工作

```less
body {
  width: 15rem;
  margin: 0 auto;
  min-width: 320px;
  line-height: 1.5;
  font-family: Arial, Helvetica, STHeiTi, sans-serif;
  background: #f2f2f2;
}
```

## header

思路: 看苏宁的写法

+ 首先一个div作为背景脱标了absolute写在下面
+ 然后用两个div, 一个是上半部分, 一个下面装个表单
+ 上下都用flex, 上半部分都说a包裹img, 下半部分放大镜是背景图实现的, 给了一个absolute
+ **重点是, 假设给的设计稿是750px, 要求切15等份, 那么一份就是50px, 设置less变量@baseFont: 50px;**
  **量取设计稿的px之后, 比如说36px的按钮, 那就是 (36rem / @baseFont), 就会转化成rem**
  **注意 #baseFont应该跟着设计稿计算出来在设置, 要和设计稿尺寸统一, 就可以算出rem, 之后无论什么尺寸, 都是按照比例缩放的.**

成果:

![image-20210312182537672](https://ebcode.oss-cn-shanghai.aliyuncs.com/img/image-20210312182537672.png)

