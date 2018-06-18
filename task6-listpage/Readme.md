# 任务六、 护工列表页

## 今天完成的事情

1.规划任务六
2.完成基本界面编写

## 明天计划的事情

- [x] 限制最小宽度
- [x] 使用雪碧图替换当前的多张图片引入
- [x] 完成模拟下拉框编写
- [x] 屏幕过窄时，列表项左边文字被截断出现省略号
- [x] 复习之前的代码规范，优化代码
- [x] 查看验收标准
- [x] 查看深度思考

## 遇到的问题

## 收获

### 一、任务六分析

1.页面原生CSS分块：

- header
  - 设计：
    - .topbar: fixed, 定高.可部分套用task3的topbar
      - tab*2(找雇主、找护工)位置center，location logo右绝对
    - .conditionbar: 暂定fixed, 定高
      - select*3故可定width百分比并使用flex， 小竖杠用border-left&first-child
      - 下拉内容简单字符填写
  - 实现：
    - .topic: topbar-switch需要将里面的a标签设置inline-block来撑高背景，并用active做激活样式.
- main
  - 设计：
    - section.service-list
      - div.service-item
        - p.item-label: img+span，无特效.
        - item-data：flex(justify-content: space-between), datedata & pricedata(red span+icon)
  - 实现：
    - 基本与设计相同
- div.bottombar: fixed, 定高. 可部分套用task3的topbar
  - 设计：
    - a*3,用flex主轴居中+交叉轴居中
    - 中间div.bottombar-middlebtn用background画圆，div.bottombar-middlebtn里面用img填图片，使其垂直水平居中
  - 实现：
    - 中间的按钮图片：一开始设line-height&vertical-align：middle, 以为居中了但效果靠下, 想起张鑫旭大神的[vertical-algn&line-height好基友](http://www.zhangxinxu.com/wordpress/2015/08/css-deep-understand-vertical-align-and-line-height/), 把div.bottombar-middlebtn的font-size改为0, 将文本中线和绝对中线重合，完成垂直居中.

    ![效果图](effect_pic/effect_result.png)
    - CSS实现下拉菜单：设置好item-title的line-height, 新建ul>li, 使其display:none & absolute, 当hover时display:block，搞定.
    - 省略号：[关于文字内容溢出用点点点(…)省略号表示](https://www.zhangxinxu.com/wordpress/2009/09/%E5%85%B3%E4%BA%8E%E6%96%87%E5%AD%97%E5%86%85%E5%AE%B9%E6%BA%A2%E5%87%BA%E7%94%A8%E7%82%B9%E7%82%B9%E7%82%B9-%E7%9C%81%E7%95%A5%E5%8F%B7%E8%A1%A8%E7%A4%BA/)
      - 最简单：定width,设置white-space + text-overflow + overflow

2.深度思考

- 1).去除inline-block间距有哪几种方法？ 参考：[去除inline-block元素间间距的N种方法](https://www.zhangxinxu.com/wordpress/2012/04/inline-block-space-remove-%E5%8E%BB%E9%99%A4%E9%97%B4%E8%B7%9D/)

  - 移除空格： 元素标签中间的空格去掉(缺点：html变丑)
  - 使用margin负值：通过设置复制去间隙(缺点：手段hack & 环境不确定，故不通用)
  - 让闭合标签吃胶囊：去掉前几个元素的结束标签，只留下最后一个结束标签(简单实用)
  - font-size:0: 已废弃，由于Chrome最小字体支持有限制。
  - letter-spacing: 缩小inline-block元素父级元素的字符间距
  - word-spacing: 缩小inline-block元素父级元素的单词间距
  - yui3:
    ``` css
    .yui3-g { /* 设置父级元素的字符间距，保证浏览器兼容性 */
        letter-spacing: -0.31em; /* webkit */
        *letter-spacing: normal; /* IE < 8 重置 */
        word-spacing: -0.43em; /* IE < 8 && gecko */
    }

    .yui3-u {
        display: inline-block;
        zoom: 1; *display: inline; /* IE < 8: 伪造 inline-block */
        letter-spacing: normal;
        word-spacing: normal;
        vertical-align: top;
    }
    ```
  - RayM提供的：
    ``` css
    li {
        display:inline-block;
        background: orange;
        padding:10px;
        word-spacing:0;
        }
    ul {  /* 设置父级元素的字符间距，保证浏览器兼容性 */
        width:100%;
        display:table;  /* 调教webkit*/
        word-spacing:-1em;
    }

    .nav li { *display:inline;}
    ```

- 2).css有哪些属性可以继承？ 参考：[CSS中可继承的属性有哪些](https://www.nowcoder.com/questionTerminal/0c76b5ff84fd4814b4ba4d45af3185b6?source=relative)

  - Tip1：每个CSS属性定义的概述都有指明属性是默认继承的还是不继承的（"Inherited: Yes|no"）
  - Tip2: 可以继承的属性一般是颜色、文字、字体间距、行高、对齐方式 & 列表样式
    - 所有元素可继承：visibility(隐藏父元素，其下所有隐藏) & cursor（button及其字体鼠标样式相同）
    - 内联元素可继承：
      - 颜色：color
      - 文字：font、font-family、font-size、font-style、font-variant、font-weight
      - 字体间距：letter-spacing、word-spacing、white-space
      - 行高：line-height
      - 样式：text-decoration、text-transform、direction
    - 块状元素可继承：text-indent & text-align
    - 列表元素可继承: list-style、list-style-type、list-style-position、list-style-image