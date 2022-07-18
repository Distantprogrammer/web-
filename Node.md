# Node 

### 终端中的快捷键

- 使用 **↑** 键，可以快速定位到上一次执行的命令 
- 输入 **node 文件夹** 命令 执行文件
- 使用 **tab** 键，能够快速补全路径 
- 使用 **esc** 键，能够快速清空当前已输入的命令
- 输入 **cls** 命令，可以清空终端
- 输入 **cd 文件夹** 命令，进入文件夹 
- 输入 **cd..** 命令，退出文件夹
- 输入 **md 文件夹名** 命令 创建文件夹
- 输入 **del 文件夹** 命令 删除文件夹
- 退出终端 **exit**
- 创建文件 **notepad 文件名**

### fs 文件系统模块

如果在JavaScript中使用fs模块，就必须引入它

```javascript
const fs = require('fs')
```



#### 读取指定文件内容

- ##### 异步地读取文件的全部内容

语法：`fs.readFile(path[, options], callback)`

参数：

|        参数名         | 参数类型 | 是否必选 |                       说明                        |
| :-------------------: | :------: | :------: | :-----------------------------------------------: |
|         path          |  String  |    是    |                   操作文件路径                    |
|        options        |  String  |    否    |     现在只用于指定编码格式未指定默认为`utf`-8     |
| callback（err，data） | Function |    是    | 回调函数，`err`：错误时返回，`data`：获取到的数据 |

实列：

```javascript
const fs = require('fs');
fs.readFile('01.js','utf-8',(err,dataStr)=>{
    if(err) return console.log('读取不到文件');
    console.log('读取到的文件为：',dataStr);
    // console.log(err);
    // console.log(dataStr);
})
```

- ##### 同步地读取文件的全部内容

语法：`fs.readFileSync(path[, options])`

参数：

| 参数名  | 参数类型 | 是否必选 |                   说明                    |
| :-----: | :------: | :------: | :---------------------------------------: |
|  path   |  String  |    是    |               操作文件路径                |
| options |  String  |    否    | 现在只用于指定编码格式未指定默认为`utf`-8 |

实列：

```javascript
const fs = require('fs');
fs.readFileSync('01.js','utf-8')
```



#### 指定文件写入内容

语法：`fs.writeFile(file, data[, options], callback)`

参数：

|    参数名     | 参数类型 | 是否必选 |                   说明                    |
| :-----------: | :------: | :------: | :---------------------------------------: |
|     path      |  String  |    是    |               写入文件路径                |
|     data      |   All    |    是    |                写入的文本                 |
|    options    |  String  |    否    | 现在只用于指定编码格式未指定默认为`utf`-8 |
| callback(err) | Function |    是    |               err：报错返回               |

注意：写入路径是新的就会创建文件 ， 旧的就修改文件，不可以创建文件夹

实列：

```javascript
const fs = require('fs');
// fs.writeFile(路径，写入的内容，配置项，callback)
//写入路径是新的就会创建文件 ， 旧的就修改文件
//不可以创建文件夹
fs.writeFile('./word.txt','测试','utf-8',err=>{
    if(err) return console.log('写入错误');
    console.log(err.message);
   console.log('写入成功');
})
```

#### fs 模块 - 路径动态拼接的问题

语法：`__dirname`

作用：表示文件所在当前路径



###  path 路径模块

#### 路径拼接

语法：`path.join([...paths])`

参数：`...paths`路径片段的序列

返回值：`string`

```javascript
path.join('/foo', 'bar', 'baz/asdf', 'quux', '..');
// 返回: '/foo/bar/baz/asdf
```



#### 获取路径文件名

语法：`path.basename(path[, ext])`

参数：`path`：表示一个路径的字符串，`ext`： 表示文件扩展名

返回值：`string`

```javascript
path.basename('/foo/bar/baz/asdf/quux.html');
// 返回: 'quux.html'

path.basename('/foo/bar/baz/asdf/quux.html', '.html');
// 返回: 'quux'
```



#### 获取路径文件扩展名

语法：`path.extname(path)`

参数：`path`：表示一个路径的字符串

返回值：`String`扩展名字符串

```javascript
path.extname('index.html');
// 返回: '.html'

path.extname('index.coffee.md');
// 返回: '.md'

path.extname('index.');
// 返回: '.'

path.extname('index');
// 返回: ''

path.extname('.index');
// 返回: ''

path.extname('.index.md');
// 返回: '.md'
```



### http模块

#### 创建最基本的 web 服务器

##### 创建 web 服务器的基本步骤

1. 导入 http 模块

   语法：`const http = require('http')`

2. 创建 web 服务器实例

   语法：`let app =http.createServer()`

3. 为服务器实例绑定 request 事件，监听客户端的请求

   语法：`app.on('request',(req,res){})`

   参数：req ：是请求对象 包含客服端相关的数据和属性，res：响应对象 包含服务端相关的数据和属性 

   扩展：

   | res                                                       |                      | req          |                                  |
   | --------------------------------------------------------- | -------------------- | ------------ | -------------------------------- |
   | `res.end('123')`                                          | 向客户端发送123      | `req.url`    | 客户端的请求`url`地址            |
   | `res.setHeader('Content-Type','text/html;charset=utf-8')` | 解决前端中文乱码问题 | `req.method` | 客户端的请求类型 `get`、`post`等 |
   |                                                           |                      |              |                                  |

   

4. 启动服务器

   语法：`app.listen(端口号,回调函数)`

   说明：端口号不设置默认为80

5. 实列

   ```javascript
   const http = require('http')
   let app = http.createServer()
   // app.on('request',()=>{
   //     console.log('111');
   // })
   app.addListener('request', (req, res) => {
       console.log(req.url, req.method);
       res.end('cnm')
       console.log(11);
   })
   app.listen(12, () => {
       console.log(333);
   })
   ```





### 模块化

#### 模块化的好处

编程领域中的模块化，就是遵守固定的规则，把一个大文件拆成独立并互相依赖的多个小模块。 

把代码进行模块化拆分的好处： 

-  提高了代码的复用性 
-  提高了代码的可维护性
-  可以实现按需加载

###  Node.js 中的模块化

#### Node.js中模块的分类

Node.js 中根据模块来源的不同，将模块分为了 3 大类，分别是： 

- 内置模块（内置模块是由 Node.js 官方提供的，例如 fs、path、http 等）
- 自定义模块（用户创建的每个 .js 文件，都是自定义模块） 
- 第三方模块（由第三方开发出来的模块，并非官方提供的内置模块，也不是用户创建的自定义模块，使用前需要先下载

#### 如何加载模块

使用 require() 方法加载其它模块时，会执行被加载模块中的代码

<img src="C:\Users\唐\Desktop\笔记\images\Node\如何加载模块.png" style="zoom:67%;" />

#### Node.js 中的模块作用域

描述：和函数作用域类似，在自定义模块中定义的**变量**、**方法**等成员，只能在当前模块内被访问，这种模块级别的访问限制，叫做模块作用域

好处：防止了全局变量污染的问题

####  向外共享模块作用域中的成员

module 对象

module.exports 对象

共享成员时的注意点

 exports 对象

 exports 和 module.exports 的使用误区

Node.js 中的模块化规范

## npm与包