# Ajax

### 客户端与服务器

#### 服务器

上网过程中，负责 存放和对外提供资源 的电脑，叫做服务器

#### 客户端

在上网过程中，负责 获取和消费资源 的电脑，叫做客户端

### URL地址的概念&组成

URL的概念

URL（全称是 `UniformResourceLocator` ） 中文叫 统一资源定位符，用于标识互联网上每个资源的唯 一存放位置。浏览器只有通过URL地址，才能正确定位资源的存放位置，从而成功访问到对应的资源

URL的组成

- 客户端与服务器之间的 **通信协议** 

- 存有该资源的 **服务器名称** 

- 资源在服务器上 **具体的存放位置**


<img src="C:\Users\唐\Desktop\笔记\images\ajax\URL的组成.png" alt="URL的组成" style="zoom:50%; float: left;" />

### 资源的请求方式

客户端请求服务器时，请求的方式 有很多种，最常见的两种请求方式分别是 **get** 和 **post** 请求

#### get 请求 

通常用于 获取服务器资源（要资源） 例如：根据 URL 地址，从服务器获取 `HTML` 文件、 `css` 文件、 `js` 文件、图片文件、数据资源等 

#### post 请求 

通常用于 向服务器提交数据（送资源） 例如：登录时，向服务器 提交登录信息、注册时向服务器 提交注册信息、添加用户时向服务器 提 交用户信息等各种 数据提交操作

### 什么是Ajax

`Ajax` 的全称是 `Asynchronous JavaScript And XML` （异步 `JavaScript` 和 `xml` ） 通俗理解：在网页中利用 `XMLHttpRequest` 对象和服务器进行数据交互的方式，就是 `Ajax`

### jQuery中的Ajax

#### $.get() 函数介绍

语法：`$.get(url,[data],[callback],[type])`

作用：通过远程 `HTTP` `GET` 请求载入信息。

参数：

|  参数名  | 参数类型 | 是否必选 |                             说明                             |
| :------: | :------: | :------: | :----------------------------------------------------------: |
|   url    |  string  |    是    |                       请求的资源的地址                       |
|   data   |  object  |    否    |              请求资源期间携带的`Key/value`参数               |
| callback | function |    否    |                      请求完成时回调函数                      |
|   type   |  string  |    否    | 返回内容格式，`xml`, `html`, `script`, `json`, `text`, `_default` |

注意：这是一个简单的 GET 请求功能以取代复杂 `$.ajax` 。请求成功时可调用回调函数。如果需要在出错时执行函数，请使用 `$.ajax`。

实列：

1. $.get()发起不带参数的请求

   直接提供给 请求的 URL 地址 和 请求成功之后的回调函数 即 可

   ```javascript
   $.get('http://ajax-base-api-t.itheima.net/api/getbooks',function(res){
         console.log(res);
       })
   ```

   

2. $.get()发起携带参数的请求

   使用 $.get() 发起携带参数的请求，那么携带的参数应该写在第二个参数的位置

   ```javascript
    $.get('http://ajax-base-api-t.itheima.net/api/getbooks',{id:3},function(res){
         console.log(res);
        })
   ```

   

#### $.post() 函数介绍

语法：`$.post(url, [data], [callback], [type])`

作用：通过远程 `HTTP` `POST` 请求载入信息。

参数：

|  参数名  | 参数类型 | 是否必选 |                             说明                             |
| :------: | :------: | :------: | :----------------------------------------------------------: |
|   url    |  string  |    是    |                         发送请求地址                         |
|   data   |  object  |    否    |                   待发送 `Key/value` 参数                    |
| callback | function |    否    |                      发送成功时回调函数                      |
|   type   |  string  |    否    | 返回内容格式，`xml`, `html`, `script`, `json`, `text`, `_default` |

注意：这是一个简单的 `POST` 请求功能以取代复杂 `$.ajax` 。请求成功时可调用回调函数。如果需要在出错时执行函数，请使用 `$.ajax`。

实列：
$.post() 向服务器提交数据：

```javascript
$.post('http://ajax-base-api-t.itheima.net/api/addbook',{ bookname:'红楼梦',author:'不详',publisher:'出版社'},function (res) {
        console.log(res);
        })
```



#### $.ajax() 函数介绍

相比于 $.get() 和 $.post() 函数， jQuery 中提供的 $.ajax() 函数，是一个功能比较综合的函 数，它允许我们对 Ajax 请求进行更详细的配置

语法：

```javascript
 $.ajax({
      type:'',//请求方式 如 get 或 post
     	url:'',//请求的 URL 地址
      data:{ },//携带的数据
   		success:function(res){ }  //请求成功后的回调函数
      })
```

- **$.ajax() 发起 get 请求**

```javascript
$.ajax({
   url:'http://ajax-base-api-t.itheima.net/api/getbooks',
   type:'get',
   data:{
     bookname:'红楼梦',
     author:'不详'
   }
 })
```

- **$.ajax 发起 post 请求**

```javascript
$.ajax({
   url:'http://ajax-base-api-t.itheima.net/api/addbook',
   type:'post',
   data:{
    bookname:'红楼梦',
     author:'不详',
     publisher:'出版社'
   }
 })
```



## 接口

#### 接口的概念

使用 `Ajax` 请求数据时，被请求的 `URL` 地址，就叫做 数据接口（简称接口）。同时，每个接口必须有 请求方式。

接口测试工具[PostMan](https://www.postman.com/)

#### 接口文档组成

| 参数     | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| 接口名称 | 用来标识各个接口的简单说明，如 登录接口，获取图书列表接口    |
| 接口URL  | 接口的调用地址                                               |
| 调用方式 | 接口的调用方式，如 GET 或者 POST                             |
| 参数格式 | 接口需要传递的参数，每个参数必须包含 参数名称、参数类型、是否必选、参数说明 这4项内容 |
| 响应格式 | 接口的返回值的详细描述，一般包含数据名称、数据类型、说明3项内容 |
| 返回示列 | 通过对象的形式，列举服务器返回数据的结构                     |

#### `<form>` 标签的属性

- **action**

作用：`action` 属性用来规定当提交表单时，向何处发送表单数据

填入值：`action` 属性的值应该是后端提供的一个URL地址，

- **target**

作用：target 属性用来规定 在何处打开 action URL

参数：

|    值     | 描述               |
| :-------: | :----------------- |
|  _blank   | 在新窗口中打开     |
|   _self   | 默认，在同窗口打开 |
|  _parent  | 在父窗口打开       |
|   _top    | 在整个窗口打开     |
| framename | 在指定的窗口打开   |

- **method**

作用：规定 以何种方式 把表单数据提交到 action URL

参数：

|  值  | 描述                                                      |
| :--: | --------------------------------------------------------- |
| get  | 默认，get 方式适合用来提交少量的，简单的数据              |
| post | post 方式适合用来提交大量的，复杂的，或包含文件上传的数据 |

- **enctype**

作用：规定在 发送表单数据之前如何对数据进行编码

参数：

|                值                 | 描述                                                       |
| :-------------------------------: | :--------------------------------------------------------- |
| application/x-www-form-urlencoded | 默认，发送前编码所有字符                                   |
|        multipart/form-data        | 不对字符编码，在使用包含文件上传控件的表单时，必须使用该值 |
|            text/plain             | 空格转换为“ + ”加号，但不对特殊字符编码                    |

#### 阻止表单默认提交行为

1. `e.preventDafault()`
2. `return false`

#### jQuery快速获取表单数据

serialize()

语法：`$(form表单).serialize()`

作用： 可以一次性获取表单的数据

**注意：**在使用 **serialize()** 函数快速获取表单数据时，必须为每个表单元素添加 **name** 属性

示例：

```javascript
/*<form action="/login" id="f1">
    <input type="text" name="user_name" />
    <input type="password" name="password" />
    <button type="submit">提交</button>
  </form> */
$('#f1').serialize()
//user_name=用户名的值password=密码的值
```

### 模板引擎

[安装地址](http://aui.github.io/art-template/zh-cn/docs/installation.html)

#### 基本使用

- 导入js

  ```html
  <script src="./lib/template-web.js"></script>
  ```

- 定义数据

  ```javascript
  var data = { name: 'zs', age: 20}
  ```

  

- 定义模板

  - 1. 必须定义带`script`标签中，把type属性改成`text/html`
    2. 给模板添加`id`
    3. 模板里面如果需要使用到传入的数据，利用 {{}} 来实现

    ```html
    <script type="text/html" id="tpl-user">
         <h1>{{name}} ------ {{age}}</h1>
    </script>
    ```

- 调用template函数

  函数的返回值就是拼接好的模板字符串

  ```javascript
  var htmlStr = template('tpl-user', data)
  ```

- 渲染HTML结构

  ```javascript
  $('#container').html(htmlStr)
  ```

#### 标准语法

- 输出

  在 {{}} 语法中，可以进行 变量 的输出，对象属性的输出，三元表达式输出，逻辑或输出，加减乘除等 表达式输出

  ```hmtl
  {{value}}
  {{obj.key}}
  {{obj['key']}}
  {{a ? b : c}}
  {{a || b}}
  {{a+ b}}
  ```

- 原文输出

  如果输出的 value 值中，包含了 HTML 标签结构，则需要使用原文输出语法，才能保证HTML标签被正 常渲染

  ```html
  {{@ value}}
  ```

- 条件输出

  如果要实现条件输出，则可以在 {{}} 中使用 if...else if.../if 的方式，进行按需输出

  ```html
  {{if value}} 内容 {{/if}}
  {{if v1}} 内容 {{else if v2}} 内容 {{/if}}
  ```

- 循环输出

  ```html
  {{each arr}}
  			{{$index}}  {{$value}}
  {{/each}}
  ```

- 过滤器

  ```html
  {{value | filterName}}
  ```

  ```javascript
  template.defaults.mports.filterName = function(value){
    return 处理的结果
  }
  ```



## 元素JS中的Ajax(XMLHttpRequest)





## JSON

**语法**：{ key: value, key: value, … }

**参数**：`key` 必须是使用英文的双引号包裹的字符串 。`value` 的数据类型可以是**数字**、**字符串**、**布尔值**、**null**、**数组**、**对象**6种类型

**优点**：更小、更快、更易解析

**作用**：在计算机与网络之间存储和传输数据

**本质**：用字符串来表示`JavaScript`对象数据或数组数据

**注意**：

- 属性名(`key`)必须使用双引号包裹 

- 字符串类型的值必须使用双引号包裹 

- `JSON` 中不允许使用单引号表示字符串 

- `JSON` 中不能写注释 

- `JSON` 的最外层必须是对象或数组格式 

- 不能使用 `undefined` 或函数作为 `JSON` 的值

```javascript
//对象
const obj = {
            a: 'Hello',
            b: 'World'
        }
//json字符串
const json = {
            "a": "Hello",
            "b": "World"
        }
```

#### JSON和JS对象的互转

##### `JSON.parse()` 

**语法**：`JSON.parse(text[, reviver])`

**参数**：**text**:必需， 一个有效的 JSON 字符串。**reviver:** 可选，一个转换结果的函数， 将为对象的每个成员调用此函数

要实现从 JSON 字符串转换为 JS 对象，使用 `JSON.parse()` 方法

```json
var obj = JSON.parse('{"a": "Hello","b": "World"}');
```

##### `JSON.stringify()` 

**语法**：`JSON.stringify(value[, replacer[, space]])`

**参数**：**value**:必需， 要转换的 JavaScript 值（通常为对象或数组）。**replacer:**可选。用于转换结果的函数或数组。**space:**可选，文本添加缩进、空格和换行符，`space` 也可以使用非数字，如：`\t`。	

要实现从 JS 对象转换为 JSON 字符串，使用 `JSON.stringify()` 方法

```json
var myJSON = JSON.stringify(obj)
```

##### 序列化和反序列化 

- 把数据对象 转换为 字符串的过程，叫做序列化，例如：调用 `JSON.stringify()` 函数的操作，叫做 `JSON` 序列化。

- 把字符串 转换为 数据对象的过程，叫做反序列化，例如：调用 `JSON.parse()` 函数的操作，叫做 JSON 反序列化。

#### `XMLHttpRequest Level2`的新功能

`var xhr = new XMLHttpRequest();`

##### 设置HTTP请求时限(`timeout`)

**语法**：

1. `xhr.timeout=time` // 超时时间，单位是毫秒
2. `xhr.onload = function ()` { // 请求完成。在此进行处理。};
3. `xhr.ontimeout = function (e)` { // `XMLHttpRequest` 超时。在此做某事。};

**作用**：`Ajax` 操作很耗时，可以设置 `HTTP` 请求的时限

**注意**：不可给同步请求使用超时。

**实列**：

```javascript
var xhr = new XMLHttpRequest();
xhr.open('GET', '/server', true);

xhr.timeout = 2000; // 超时时间，单位是毫秒

xhr.onload = function () {
  // 请求完成。在此进行处理。
};

xhr.ontimeout = function (e) {
  // XMLHttpRequest 超时。在此做某事。
};

xhr.send();
```



##### 管理表单数据(`FormData`)

**语法**：`var formData = new FormData(form)`

**作用**：收集表单的所有数据的键值对 `key/value` 

**参数**：form：一个 HTML 上的[``](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/form)表单元素

**注意**：使用了`FormData()`的`XMLHttpRequest（XHR）`的`post`请求不需要写 `xhr.setRequestHeader('Content-Type','application/x-www-form-urlencoded')`

**实列**：

```javascript
var myForm = document.getElementById('myForm');
formData = new FormData(myForm);
```

**方法**： 

- append()

  语法：

  1. `formData.append(name, value);`
  2. `formData.append(name, value, filename);`

  作用：添加新值到

  参数：name：`value`中包含的数据对应的表单名称。value：表单的值。filename（可选）：[查看](https://developer.mozilla.org/zh-CN/docs/Web/API/FormData/append)

  返回值：空

  ```javascript
  var formData = new FormData(); 
  formData.append('username', 'Chris');
  formData.append('userpic', myFileInput.files[0], 'chris.jpg');
  ```

  

- delete()

  语法：`formData.delete(name);`

  作用：`FormData` 对象中删除指定键，即 key，和它对应的值，即 value

  参数：name：要删除的键（`Key`）的名字。

  返回值：空

  ```javascript
  formData.delete('username');
  ```

  

- entries()

  语法：`formData.entries`();

  作用：此对象可以遍历访问 `FormData` 中的键值对。

  参数：无

  返回值：返回 [`iterator`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Iteration_protocols)。

  实列：

  ```javascript
  // Create a test FormData object
  var formData = new FormData();
  formData.append('key1', 'value1');
  formData.append('key2', 'value2');
  
  // Display the key/value pairs
  for(var pair of formData.entries()) {
     console.log(pair[0]+ ', '+ pair[1]);
  }
  
  ```

  

- get()

  语法：`formData.get(name)`

  作用：`get()`方法用于返回`FormData`对象中和指定的键关联的第一个值，如果你想要返回和指定键关联的全部值，那么可以使用`getAll()`方法。

  参数：name：将要获取值的键名。

  返回值：包含值的`FormData`对象中的`Value`

  实列：

  ```javascript
  var formData = new FormData();
  formData.append('username', 'Chris');
  formData.append('username', 'Bob');
  formData.get('username'); // Returns "Chris"
  ```

  

- getAll()

  语法：`formData.getAll(name)`;

  作用：`getAll()`方法会返回该 `FormData` 对象指定 key 的所有值。

  参数：要检索的 key 名称。

  返回值：一个 `FormData`对象中所有`Value`的数组。

  实列：

  ```javascript
  var formData = new FormData();
  formData.append('username', 'Chris');
  formData.append('username', 'Bob');
  formData.getAll('username'); // Returns ["Chris", "Bob"]
  ```

  

- has()

  语法：formData.has(name);

  作法：检查`FormData`对象中是否有某个值

  参数：要查询的 `key` 名称。

  返回值：`Boolean`

  实列：

  ```javascript
  formData.has(name);
  formData.has('username'); // Returns false
  formData.append('username', 'Chris');
  formData.has('username'); // Returns true
  ```

  

- keys()

  语法：`formData.keys()`;

  作用：遍历了该 `formData`  对象里的所有 `key`。

  参数：无

  返回值：所有的`key`迭代器

  实列：

  ```javascript
  // 先创建一个 FormData 对象
  var formData = new FormData();
  formData.append('key1', 'value1');
  formData.append('key2', 'value2');
  
  // 输出所有的 key
  for (var key of formData.keys()) {
     console.log(key);
  }
  //key1
  //key2
  ```

  

- set()

  语法：

  1. `formData.set(name, value)`;
  2. `formData.set(name, value, filename)`;

  作用：`FormData` `对象里的某个` `key` `设置一个新的值，如果该` `key` `不存在，则添加。filename：

  参数：name：字段名称。value：字段的值，如果不是这两个指定的类型，其将被转成一个字符串。当第二个参数传递的是一个 blob 对象（`Blob`）或者 file 对象（`File`），filename 参数就代表传给服务端的文件名（一个 `USVString`)。 Blob对象的默认文件名是 "blob"，`File`对象的默认文件名则为其“name”属性

  返回值：无

  实列：

  ```javascript
  var formData = new FormData(); // Currently empty
  formData.set('username', 'Chris');
  formData.set('userpic', myFileInput.files[0], 'chris.jpg');
  ```

  

- values()

  语法：`formData.values()`

  作用：遍历该对象中所有值(`value`)的 

  参数：无

  返回值：返回一个`迭代器`

  实列：

  ```javascript
  //创建一个 FormData 测试对象
  var formData = new FormData();
  formData.append('key1', 'value1');
  formData.append('key2', 'value2');
  
  //显示值
  for (var value of formData.values()) {
     console.log(value);
  }
  //value1
  //value2
  ```

  

###### 获取文件上传进度

语法：`XMLHttpRequest.upload`

作用：可以通过对其绑定事件来追踪它的进度

参数：

| 事件          | 相应属性的信息类型               |
| ------------- | -------------------------------- |
| `onloadstart` | 获取开始                         |
| `onprogress`  | 数据传输进行中                   |
| `onabort`     | 获取操作终止                     |
| `onerror`     | 获取失败                         |
| `onload`      | 获取成功                         |
| `ontimeout`   | 获取操作在用户规定的时间内未完成 |
| `onloadend`   | 获取完成（不论成功与否）         |

实列：

```javascript
 xhr.upload.onprogress = function(e){
                if(e.lengthComputable){
                }
```





#### jQuery实现loading效果

##### 监听请求开始

**语法**：`ajaxStart(callback)`

**作用**：`Ajax` 请求开始时，可以调用函数。

**参数**：`callback`回调函数

**注意**：`$(document).ajaxStart()` 函数会监听当前文档内所有的 Ajax 请求。

**效果相似**：`beforeSend(XHR)`

```javascript
$(document).ajaxStart(function() {})
```



##### 监听请求结束

**语法**：`ajaxStop(callback)`

**作用**：`Ajax` 请求结束时，可以调用函数。

**参数**：`callback`回调函数

**注意**：`$(document).ajaxStop()` 函数会监听当前文档内所有的 Ajax 请求。

**效果相似**：`complete(XHR, TS)`

```javascript
$(document).ajaxStop(function() {})
```



## axios

#### 什么是axios

- `Axios` 是专注于网络数据请求的库。 
- 相比于原生的 `XMLHttpRequest` 对象， `axios` 简单易用。
- 相比于 `jQuery` ， `axios` 更加轻量化，只专注于网络数据请求。

#### axios发起GET请求

语法：axios.get('url', { params: { `key`,`value` } }).then(callback)

参数：`url`:请求地址，`params`：get参数，`callback`：回调函数

注意：**get**填参数需要加**params**，**post**不需要

```javascript
let paramsObj={ name: 'zs', age: 20 }
axios.get(url, { params: paramsObj }).then(function(res) {
// res.data 是服务器返回的数据
var result = res.data
console.log(res)
})
```

`axios`发起POST请求

语法：axios.post('url', {`key`, `value`}).then(callback)

参数：`url`:请求地址，`params`：get参数，`callback`：回调函数

注意：**get**填参数需要加**params**，**post**不需要

```javascript
// 要提交到服务器的数据
var dataObj = { name: 'zs', age: 20 }
// 调用 axios.post() 发起 POST 请求
axios.post(url, dataObj).then(function(res) {
// res.data 是服务器返回的数据
var result = res.data
console.log(result)
})
```

#### 直接使用`axios`发起请求

**语法**：

```javascript
axios({
method: '请求类型',
url: '请求的URL地址',
data: { /* POST数据 */ },
params: { /* GET参数 */ }
}).then(callback)
```

**实列**：

发起`get`请求

```javascript
var paramsData = { name: '钢铁侠', age: 35 }
axios({
method: 'GET',
url: 请求的URL地址,
params: paramsData
})
 .then(function (res) {
console.log(res.data)
})
```

发起`post`请求

```javascript
axios({
method: 'POST',
url: '请求的URL地址',
data: {
name: '娃哈哈',
age: 18,
gender: '女'
}
})
 .then(function (res) {
console.log(res.data)
})
```

## 同源策略

#### 什么是同源

本质：两个页面的**协议**、**域名**、**端口**都相同则为同源

作用：浏览器端的网络安全功能，用于隔离潜在恶意文件的重要安全机制

注意：如果域名后面没有端口，就使用默认端口80

实列：

1. ```text
   1. a浏览器中的网页对b服务器发起请求
   2. b服务器处理响应给a浏览器
   3. a浏览器接收数据，进行拦截检查，检测是否同源
   4. 如果同源，把数据给网页。不是就不给
   ```

#### 什么是跨域

本质：只要不是同源就是跨域

原因：浏览器的同源策略不允许非同源的 URL 之间进行资源的交互

跨域两种解决办法：

1. jsonp  临时解决方案 ，前后一起配合。 **缺点**：只可以发起`get`请求
2. cors  前端不管，后端配置。**缺点**：兼容性

#### js 中JSONP 的实现过程

手动添加`<script>`标签 修改里面的src

实列：

```html
<script>
function success(data) {
console.log('获取到了data数据：')
console.log(data)
}
</script>
<script src="http://ajax.frontend.itheima.net:3006/api/jsonp?callback=success&name=zs&age=20"></script>
```



#### jQuery 中JSONP 的实现过程

在发起 JSONP 请求的时候，动态向`<header>` 中 append 一个 `<script>` 标签

在 JSONP 请求成功以后，动态从 <`header`>中移除刚才 append 进去的 <`script`>标签
