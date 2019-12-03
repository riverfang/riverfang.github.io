---
title: markdown常用语法
tag: [markdown]
---

marckdown常用语法
--
> #### 换行

```math
E = mc^2
```

```
需要换行时在后面输入两个空格，然后回车
```
> ### 标题

```
# 这是H1
## 这个是H2
### 这个是H3
```
> ### 区块引用

```
使用>的引用方式，例如: > 引用的内容
```
> ### 列表
```
1. 有序列表
   直接在数字后面加上点号
2. 无序列表
   在每一行前面加上*号、+号或者-号即可
```
> ### 分区代码块
    四个空格(或一个tab)，或者代码区间上下边缘使用反单引号进行代码区间的隔离  
> ### 分割线

```
在一行中用三个或三个以上的*号或-即可输出分割线
```
<!-- more -->

> ### 区段元素
[百度一下](http://wwww.baidu.com '百度一下你就知道了')  
![我们都是追梦人](http://www.baidu.com/img/dong_ca53b94625c757745bcb2c16461eb105.gif '我们都是追梦人')


```
1. 链接
[alt text](url地址 'title')  
2. 图片
![alt text](url地址 'title')
3. 强调
将强调部分使用单*号或单_进行包裹
```
> ### 表格
header 1 | header 2 | header 3
---|---|---
row 1 col 1 | row 1 col 2 | 我们都是追梦人
row 2 col 1 | row 2 col 2 | 我的中国梦

> ### 流程图

```
基本图元
1. id + [文字描述]      表示矩形
2. id + (文字描述)      表示圆角矩形
3. id + >文字描述]      表示不对称矩形
4. id + {文字描述}      表示菱形
5. id + ((文字描述))    表示圆形
```

```
graph LR
id1[带文本的矩形]
id2(带文本的圆角矩形)
id3>带文本的不对称矩形]
id4{带文本的菱形}
id5((带文本的原型))
```
```
节点之间的关联  
1. A-->B  A带箭头指向B
2. A---B  A不带箭头指向B
3. A-.->B A用带箭头的虚线指向B
4. A-.-B  A用不带箭头的虚线指向B
5. A==>B  A用加粗箭头执行B
6. A--描述---B  A不带箭头指向B，并在中间加上文字
7. A--描述-->B   A带箭头指向B，并在中间加上文字
8. A-.描述.->B   A带箭头虚线指向B，并在中间加上文字
9. A-.描述.--B   A不带箭头的虚线指向B，并在中间加上文字
10. A==描述==>   A带粗线箭头指向B，并在中间加上文字
```

```
graph LR
A[A]-->B[B]
A1[A]---B1[B]
A2[A]-.->B2[B]
A3[A]-.-B3[B]
A4[A]==>B4[B]
A5[A]--描述---B5[B]
A6[A]--描述-->B6[B]
A7[A]-.描述.->B7[B]
A8[A]-.描述.--B8[B]
A9[A]==描述==>B9[B]
```

```
graph LR
A-->B[开始节点]
style B fill:purple,fill-opacity:0.5,stroke-dasharray: 5,stroke-width:3px,stroke:black
```
> 简易样式

```
graph LR
start[开始节点]-->decision{判断是否已经登录}

decision-->|否|d(未登录)
decision-->|是|c(已登录)
d-->stop[结束节点]
c-->stop

style start fill:#66FF66,fill-opacity:0.8
style stop fill:#F33B14,fill-opacity:0.8
style decision fill:#FFFF66,fill-opacity:0.8,stroke:red,stroke-width:3px,stroke-dasharray:5
style d fill:red,fill-opacity:0.8
style c fill:green,fill-opacity:0.8
```

> 一些案例

```
graph TD
    st[注册印象笔记]-->a
    a{是否已经购买马克飞象}
    a-->|是|b1(您已购买马克飞象可以使用markdown语法)
    a-->|否|b2(您还未能成功购买马克飞象但你可以免费试用10天)
    b1-->c[欢迎使用马克飞象]
    b2-->d{是否要购买马克飞象}
    d-->|是|e1(您已成功购买马克飞象欢迎使用)
    e1-->c
    d-->|否|e2(试用10天后将会到期欢迎购买)
    ```
    


```
title: 消息推送时序图
浏览器客户端-> web端: 请求握手建立连接
dubbo服务-> web端: 调用controller层
web端--> 浏览器客户端: 推送消息
note left dubbo服务: 数据包解析完成后，调用web端控制层(或者其他http端点)，发送需要推送的消息作为请求体
```

```javascript
var fmtDate = function (value,fmt) {
    if(!value || !fmt){
        return "";
    }
    try{
        var d = value instanceof Date ? value : (!isNaN(value) ? new Date(value) : (/([a-zA-Z])/.test(value) ? value : new Date(value.replaceAll("-","/"))));
        var o = {
            "M+": d.getMonth() + 1, //月份
            "d+": d.getDate(), //日
            "h+": d.getHours(), //小时
            "m+": d.getMinutes(), //分
            "s+": d.getSeconds(), //秒
            "q+": Math.floor((d.getMonth() + 3) / 3), //季度
            "S": d.getMilliseconds() //毫秒
        };
        if (/(y+)/.test(fmt)) fmt = fmt.replace(RegExp.$1, (d.getFullYear() + "").substr(4 - RegExp.$1.length));
        for (var k in o)
            if (new RegExp("(" + k + ")").test(fmt)) fmt = fmt.replace(RegExp.$1, (RegExp.$1.length == 1) ? (o[k]) : (("00" + o[k]).substr(("" + o[k]).length)));
        return fmt;
    }catch(e){
        return "";
    }
```

```mermaid
gantt
dateFormat  YYYY-MM-DD
title Shop项目交付计划
 
section 里程碑 0.1 
数据库设计          :active,    p1, 2016-08-15, 3d
详细设计            :           p2, after p1, 2d
 
section 里程碑 0.2
后端开发            :           p3, 2016-08-22, 20d
前端开发            :           p4, 2016-08-22, 15d
 
section 里程碑 0.3
功能测试            :       p6, after p3, 5d
上线               :       p7, after p6, 2d
交付               :       p8, afterp7, 2d

```


