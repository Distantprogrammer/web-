## Node 

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