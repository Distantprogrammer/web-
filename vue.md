# vue

## 模块打包工具（webpack）

### webpack的作用

1. 减少文件数量
2. 缩减代码体积
3. 提高浏览器打开的速度

### webpack本质

1. 第三方模块包，用于分析，并打包带代码
2. 支持所有类型文件的打包
3. 支持less/sass=>css
4. 支持ES6/7/8 => ES5
5. 压缩代码，提高加载速度

### webpack使用步骤

#### 环境准备

1.下载安装程序（更多方法请访问[webpack](https://yarn.bootcss.com/docs/install#windows-stable)）

下载一个 **.msi** 文件  使用此程序， 需要先安装**Node.js**

<img src="C:\Users\唐\Desktop\笔记\images\vue\yarn文件.png" alt="yarn文件" style="zoom:60%;" />

2.初始化包环境

创建一个 `package.json` 文件 

`package.json` 的文件中跟踪依赖关系和元数据。这是你项目的核心。它包含名称、描述和版本之类的信息，以及运行、开发以及有选择地将项目发布所需的信息。

```shell
yarn init
```

 `yarn init --yes`跳过会话

<img src="C:\Users\唐\Desktop\笔记\images\vue\初始化包环境.png" alt="初始化包环境" style="zoom:53%;" />

<img src="C:\Users\唐\Desktop\笔记\images\vue\初始化创建的文件.png" alt="初始化创建的文件" style="zoom:60%;" />

3.安装依赖包

```shell
yran add webpack webpack-cli -D
```

**为什么不直接使用webpack，而后面要加上webpack-cli 呢？**

webpack CLI 为开发人员提供了一组灵活的命令，以在**设置自定义 webpack 项目时提高速度**。从 webpack v4 开始，webpack 不需要配置文件，但开发人员通常希望根据他们的用例和需求创建更自定义的 webpack 配置。webpack CLI 通过提供一组工具来改进自定义 webpack 配置的设置来满足这些需求。

**后面的 -D 是什么呢？**

**-D**是`--save-dev`的简写，会安装在开发环境中(`production`)中的`devPendencies`中（**安装开发环境**）
**-S**是`--save`的简写，会安装在生产环境中(`development`)中的`dependencies`中（**安装生产环境**）
**-g**是`-global`的简写 ，安装模块到全局，不会在项目`node_modules`目录中保存模块包。 不会将模块依赖写入`devDependencies`或`dependencies` 节点（**安装全局**）
**i** 是 `install` 的简写，将安装包放在 `./node_modules` 下（运行 npm 命令时所在的目录），如果没有 `node_modules` 目录，会在当前执行 npm 命令的目录下生成 `node_modules` 目录

<img src="C:\Users\唐\Desktop\笔记\images\vue\安装依赖包.png" alt="安装依赖包" style="zoom:60%;" />

4.配置scripts（自定以命令）

```json
 "scripts": {
    "bulid":"webpack"
  }
```

`"bulid"` 自定义名称

<img src="C:\Users\唐\Desktop\笔记\images\vue\配置项.png" alt="配置项" style="zoom:60%;" />



#### webpack基础使用

##### 合并且压缩2个js文件



##### webpack再次打包



#### webpack入口的出口

























## @vue/cli脚手架

### @vue/cli安装

1. 全局安装@vue/cli模块包

   ```shell
   yarn global add @vue/cli
   ```

   <img src="C:\Users\唐\Desktop\笔记\images\vue\安装全局.png" style="zoom:60%;" />

2. 查看是否成功

```shell
vue -V
```

<img src="C:\Users\唐\Desktop\笔记\images\vue\查看vue版本.png" style="zoom:60%;" />

### @vue/cli 创建项目

1. 创建项目

   ```shell
   vue create 项目名
   ```

   <img src="C:\Users\唐\Desktop\笔记\images\vue\创建项目.png" style="zoom:60%;" />

   注意：项目名不能有大写字母，中文，特殊字符

2. 选择模板和包管理器

   <img src="C:\Users\唐\Desktop\笔记\images\vue\选择版本.png" alt="选择版本" style="zoom:50%;" />

   <img src="C:\Users\唐\Desktop\笔记\images\vue\安装成功.png" style="zoom:60%;" />

3. 启动

```shell
yarn serve
```

<img src="C:\Users\唐\Desktop\笔记\images\vue\运行项目.png" alt="运行项目" style="zoom:60%;" />

<img src="C:\Users\唐\Desktop\笔记\images\vue\运行成功.png" style="zoom:60%;" />

### @vue/cli 目录和代码分析

![](C:\Users\唐\Desktop\笔记\images\vue\vue目录分析.png)





## vue指令

### 插值表达式

语法：{{ 表达式 }}

参数：要在js中的data函数里声明

示例：

```vue
<template>
  <div>
    <!-- 把值赋予到标签 -->
    <h1>{{ msg }}</h1>
    <h2>{{ obj.name }}</h2>
    <h3>{{ obj.age >= 18 ? "成年了" : "未成年" }}</h3>
  </div>
</template>

<script>
export default {
  //变量在data函数return的对象上
  /* data(){
  return {
}
}*///这是固定语法 ， 数据都要到data里声明
  data() {
    return {
      msg: "Hello,Vue",
      obj: {
        name: "小vue",
        age: 5,
      },
    };
  },
};
</script>

<style>
</style>
```

![](C:\Users\唐\Desktop\笔记\images\vue\插值表达式data.png)

### Vue指令-v-bind(标签属性)

作用：给标签属性设置vue变量的值

语法：v-bind:属性名="vue变量"

简写：：属性名 = "vue变量"

示例：

```vue
<template>
  <div>
   <!-- 2.值 -->
   <a v-bind:href="url">点击去百度</a>、
   <img :src="imgURL" alt="">
  </div>
</template>

<script>
export default {
  //1.准备变量~
  data(){
    return {
      url:'http://www.baidu.com',
      imgURL:'https://www.baidu.com/img/PCtm_d9c8750bed0b3c7d089fa7d55720d6cf.png'
    }
  }
};
</script>
```

### Vue指令-v-on(绑定事件)

作用：给对象添加事件

语法：

- v-on:事件名="要执行的少量代码"
- v-on:事件名="methods中的函数名"
- v-on:事件名="methods中的函数名(实参)"
- 简写：@事件名="methods中的函数"

示例：

```vue
<template>
  <div>
    <!-- 2.值 -->
    <p>你要购买的数量：{{ count }}</p>
    <!-- 语法一 -->
    <button v-on:click="count = count + 1">+1</button>
    <!-- 语法二 -->
    <button v-on:click="addFn">+1</button>
    <!-- 语法三 -->
    <button v-on:click="addCountFn(5)">+5</button>
    <!-- 简写 -->
    <button @click="subFn">-1</button>
  </div>
</template>

<script>
export default {
  //1.准备变量~
  data() {
    return {
      count: 1,
    };
  },
  //定义函数
  methods: {
    addFn() {
      //this指向的export default的{}
      //data函数会把对象挂载到当前组件对象上
      this.count++;
    },
    subFn() {
      //this指向的export default的{}
      //data函数会把对象挂载到当前组件对象上
      this.count--;
    },
    addCountFn(num){
      this.count =this.count+num
    }
  },
};
</script>
```

### Vue指令-v-on(绑定事件)获取事件对象（e）

作用：获取事件对象(e)

语法：`@click="two(10, $event)`

- 无传参，通过形参直接接受
- 传参，通过`$event`指代事件对象传给事件处理函数

示例：

```vue
<template>
  <div>
    <!-- 2.值 -->
    <a @click="one" href="www.baidu.com">百度</a>
    <hr />
    <a @click="two(10, $event)" href="www.taobao.com">淘宝</a>
  </div>
</template>

<script>
export default {
  methdos: {
    one(e) {
      //1.事件无传值，可以直接获取获取事件对象(e)
      e.preventDefault();
    },
    two(num, e) {
      //2.事件有传参，需要手动传入$event
      e.preventDefault();
    },
  },
};
</script>

```

### Vue指令-v-on修饰符

作用：简洁的写法

语法：@事件名.修饰符="methods里函数"

列表：

- `.stop`   阻止事件冒泡
- `.prevent`   阻止默认事件
- `.once`  程序运行期间，只处罚一次事件处理函数

```vue
<template>
  <div>
    <!-- 2.值 -->
    <div @click="fatherFn">
      <p @click.stop="oneFn">.stop 阻止事件冒泡</p>
      <a href="www.baidu.com" @click.prevent.stop>百度</a>
      <p @click.once="twoFn">点击观察事件处理函数执行几次</p>
    </div>
  </div>
</template>

<script>
export default {
  methods:{
    fatherFn(){
console.log('father点击了');
    },
    oneFn(){
      console.log('p标签点击了');
    },
    twoFn(){
      console.log("p标签被点击了");
    }
  }
```

### Vue指令-v-on按键修饰符

作用：监听键盘事件

语法：@keyup.enter

示例：

```vue

```

