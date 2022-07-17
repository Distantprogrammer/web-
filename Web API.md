## Web API

### 变量声明

`var`

存在变量提升

`let`

声明变量，不会变量提升

`const`

声明常量，在确定值（地址）以后不变

### 获取DOM对象

#### 获取HTML

```javascript
document.documentElement
```



#### 获取body

```javascript
document.body
```



#### document.getElementById

语法：`document.getElementById(id)` 

作用：根据ID获取元素对象 

参数：id值，区分大小写的字符串 

返回值：元素对象 或 null  伪数组

```javascript
document.getElementById('id')不需要加#号
```



#### document.getElementsByClassName

语法：`document.getElementsByClassName('class')`

作用：根据class(类名)获取元素对象 

参数：元素的类名，区分大小写的字符串 

返回值：元素对象 或 null  伪数组

注意：上下文可以是document，也可以是一个元素。

```javascript
document.getElementsByClassName('class')不需要加.
```



#### document.getElementsByName

语法：`document.getElementsByName('name')` 

作用：根据name获取元素对象 

参数：name属性

返回值：元素对象集合（伪数组，数组元素是元素对象）

注意：上下文必须是document

```javascript
document.getElementsByName('name')
```



#### document.getElementsByTagName

语法：`document.getElementsByTagName('标签名')` 或者 `element.getElementsByTagName('标签名')`  

作用：根据标签名获取元素对象 

参数：标签名 

返回值：元素对象集合（伪数组，数组元素是元素对象）

注意：`getElementsByTagName()`获取到是动态集合，即：当页面增加了标签，这个集合中也就增加了元素。

```javascript
document.getElementsByTagName('li');
```



#### document.getElementsByTagNameNS

语法：`document.getElementsByTagNameNS(namespace, name)`

作用：根据`url`和`name`获取元素对象 

参数：`namespace`, `name`

返回值：带有指定名称和命名空间的元素集合，整个文件结构都会被搜索，包括根节点

注意：`namespace `是所要查询的元素的命名空间 URL，`name` 是所要查询的元素的名称。其中特殊字符 "*" 代表所有元素

```javascript
 document.getElementsByTagNameNS("http://www.w3.org/1999/xhtml", "p")
```



#### document.querySelector

语法：`document.querySelector('')`

作用：根据css选择器返回第一个匹配的元素

参数：一个或多个要匹配的选择器的 DOM 字符串[`DOMString`](https://developer.mozilla.org/zh-CN/docs/conflicting/Web/JavaScript/Reference/Global_Objects/String_6fa58bba0570d663099f0ae7ae8883ab)。 该字符串必须是有效的 CSS 选择器字符串

返回值： CSS 选择器匹配的第一个元素，一个 [`Element`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element)对象。如果没有匹配到，则返回 null。

注意：如果您需要与指定选择器匹配的所有元素的列表，则应该使用`querySelectorAll()`

```javascript
document.querySelector("css选择的方式")css怎样选里面就怎么填 如.box #box等
```



#### document.querySelectorAll

语法：`document.querySelector('')`

作用：根据css选择器所以的元素  

参数：一个合法的 CSS选择器 如果不是，会抛出一个 `SyntaxError` 错误

返回值： 对象是 `NodeList`（节点集合） 伪数组

注意：如果`selectors`参数中包含 CSS 伪元素，则返回的列表始终为空。

```
document.querySelectorAll("css选择的方式")
```



### 操作元素

#### 操作元素内容

##### innerHTML

将文本内容添加/更新到任意标签位置 

显示纯文本，不解析标

```javascript
document.getElementById('divA').innerHTML
```



##### innerText

 将文本内容添加/更新到任意标签位置 

会解析标签，多标签建议使用模板字符

```javascript
document.getElementById('divA').innerText
```



##### textContent

在节点上设置 `textContent` 属性的话，会删除它的所有子节点，并替换为一个具有给定值的文本节点。

使用前务必先做判断, IE8及更早版本不兼容

```javascript
document.getElementById('divA').textContent;
```

##### 扩展

作为扩展这里介绍下 还有存在三种类似属性 

 outerHTML 返回标签和内容组成的字符串  

outerText 获取元素自身, 不含子元素文本内容

#### 操作元素属性

##### 操作元素常用属性

通过 JS 设置/修改标签元素属性，比如通过 src更换 图片，最常见的属性比如： href、title、src 等

```javascript
document.querySelector('img').src='www.xxxxx.jpg';
```

#####  操作元素样式属性

###### 通过 style 属性操作CSS

语法：修改样式通过style属性引出  ，

作用：更改`html`元素的样式

参数：css样式属性

 注意：如果属性有-连接符，需要转换为小驼峰命名法  赋值的时候，需要的时候不要忘记加css单位

```javascript
document.querySelector('div').style.backgroundColor='blue';
```

###### 操作类名(className) 操作CSS

语法：操作类名(className) 操作CSS ，通过 classList 操作类控制CS

作用：如果修改的样式比较多，直接通过style属性修改比较繁琐，我们可以通过借助于css类名的形式。

参数：css类名

 注意：className是使用新值换旧值, 如果需要添加一个类,需要保留之前的类。为了解决className 容易覆盖以前的类名，我们可以通过classList方式追加和删除类名

```javascript
document.querySelector('div').className='class'  // className添加类名 不用加.
document.querySelector('div').classList.add('class')  // classList添加类名 不用加. 
document.querySelector('div').classList.remove('class')  // classList添加删除不用加.
document.querySelector('div').classList.toggle('class')  // classList添加类名删除类名 不用加. toggle有就删除没有就添加
```

##### 操作表单元素属性

通过 JS 设置/修改表单属性

布尔值 如：disabled、checked、selected

```javascript
 document.querySelector('input').disabled=false
```

文本 如：value

```javascript
 document.querySelector('input').value='填写内容'
```

#####  自定义属性

标签天生自带的属性 比如class id title等, 可以直接使用点语法操作比如： disabled、checked、selected

###### 完全自定义属性

随便设置属性

```html
<input type="text" id="txtBox" displayName="123456" />
<input type="text" id="txtBox" index="123456" />
<input type="text" id="txtBox" q="123456" />
```

`setAttribute()`设置指定元素上的某个属性值。如果属性已经存在，则更新该值；否则，使用指定的名称和值添加一个新的属性。

```javascript
element.setAttribute(name, value); //name属性名称的字符串 value属性的值/新值
```

`removeAttribute()` 从指定的元素中删除一个属性。。

```javascript
element.removeAttribute(attrName);//attrName要删除的属性名
```

`getAttribute()` 返回元素上一个指定的属性值。如果指定的属性不存在，则返回  `null` 或 `""` （空字符串）

```javascript
let attribute = element.getAttribute(attributeName);//attributeName 是你想要获取的属性值的属性名称。
```

`hasAttribute` 返回一个布尔值，指示该元素是否包含有指定的属性（attribute）

```javascript
var result = element.hasAttribute(attName);//attName 字符串，表示属性的名称
```

`Element.attributes` 属性返回该元素所有属性节点的一个实时集合

```javascript
var attr = element.attributes;
```

###### 官方规定自定义属性

html5中设置自定义属性用“data-”开头，多个字母用 “-” 连接

设置自定义属性

```html

<!-- Html5规定，给元素自定义数据属性时，属性名称以data-开头，但是真正的属性名不包括data--->
<p id="p1" data-school = "qh">清华大学</p>
<div id="p1" data-id = "qh">清华大学</div>
```

获取定义的自定义属性

 dataset 后边必须要用驼峰命名法 否则可能获取不到属性值

```javascript
<script>
    var value1=document.getElementById("p1").dataset["school"];
    console.log("value1:"+value1);
</script>
```

当然也可以用getAttribute 来获取自定义属性

```javascript
<script>
    var value2=document.getElementById("p1").getAttribute("data-school");
    alert("value2:"+value2)
</script>
```





#### 定时器

在 js 里面，有两种定时器，**倒计时定时器** 和 **间隔定时器**

时间是按照毫秒进行计算的，1000 毫秒就是 1秒钟

注意：`setInterval()` 和 `setTimeout()` 共享同一个 ID 池 。并且 `clearInterval()` 和 `clearTimeout()` 在技术上是可互换使用的

##### 定时器-间歇函数（间隔定时器）

语法：setInterval(要执行的函数，间隔多少时间)

作用：每间隔多少时间就执行一次函数

参数：`function` 是你想要在到期时间 (`delay`毫秒) 之后执行的函数。`delay` 延迟的毫秒数

 `arg1, ..., argN`当定时器过期，将被传递给 *func* 函数的附加参数

返回值：当前这个定时器是页面中的第几个定时器

注意：只要不关闭，会一直执行。参数 `delay` 会被转换成一个有符号 32 位整数。这将 `delay` 限制到了 2147483647 毫秒以内，因为它在 IDL 中被指定为一个有符号整数。

```javascript
let intervalTime = window.setInterval(function(){}, 2000);//window可以省略
```



##### 定时器-延时函数（倒计时定时器）

倒计时定时器（延时器 延时执行一次）

语法：setTimeout(function[, delay, arg1, arg2, ...]);

作用：倒计时多少时间以后执行函数

参数：`function` 是你想要在到期时间之后执行的函数。`delay` 延迟的毫秒数  `arg1, ..., argN` 附加参数，一旦定时器到期，它们会作为参数传递给`function`

返回值：当前这个定时器是页面中的第几个定时器

注意：只执行一次，就不在执行了。参数 `delay` 会被转换成一个有符号 32 位整数。这将 `delay` 限制到了 2147483647 毫秒以内，因为它在 IDL 中被指定为一个有符号整数。

```javascript
let timeoutTime= window.setTimeout(function(){}, 2000);//window可以省略
```

##### 清除定时器

```javascript
clearInterval(intervalID) //intervalID 间歇定时器的名字
```

```javascript
clearTimeout(timeoutID) //timeoutID 延时定时器的名字
```



#### 练习题目

[webAPIs 第一天测试题-pink老师 (wjx.top)](https://ks.wjx.top/vj/hwyC7n1.aspx)