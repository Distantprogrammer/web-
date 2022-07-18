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

- 使用**npm**命令

```shell
npm insatll yarn -g
```

- 下载一个 **.msi** 文件  使用此程序， 需要先安装**Node.js**


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

语法：`@keyup.enter`

示例：

```vue
<template>
  <div>
    <!-- 2.值 -->
    <input type="text" @keyup.enter="enterFn">
  </div>
</template>

<script>
export default {
  methods:{
    enterFn(){
      console.log('用户按下了回车');
    }
  }
};
</script>
```

### Vue指令-v-model（双向绑定）

作用：value属性和vue数据变量，双向绑定到一起

语法：v-model="Vue数据变量"

说明：

- 变量变化 ->视图自动同步
- 视图变化 ->变量自动同步

示例：

```vue
<template>
  <div>
    <label for="">账号</label><input type="text" v-model="username" />
    <!-- v-model
    双向数据绑定
    value属性 - vue变量 
    -->
    <hr />
    <label for="">密码</label><input type="password" v-model="pass"/>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: "",
      pass:"",
    };
  },
};
</script>
```

### Vue指令-v-model（双向绑定）绑定不同表单标签

下拉框：下拉菜单绑定到section上 

复选框：

- 遇到复选框，`v-model`绑定到各个复选框 ，
- 非数组类型  - 关联的是复选框的`checked`属性
- 数组类型   - 关联的是复选框的`value`属性

```vue
<template>
  <div>
    <!-- v-model
    双向数据绑定
    value属性 - vue变量 
    -->
    <div>
      <span>来自与：</span>
      <!-- 下拉菜单绑定到section上 -->
      <select name="" id="" v-model="from">
        <option value="北京市">北京</option>
        <option value="长沙市">长沙</option>
        <option value="武汉市">武汉</option>
        <option value="深圳市">深圳</option>
      </select>
    </div>
    <div>
      <span>爱好：</span>
      <input type="checkbox" value="抽烟" v-model="hobby" />抽烟
      <input type="checkbox" value="喝酒" v-model="hobby" />喝酒
      <input type="checkbox" value="吃肥肉" v-model="hobby" />吃肥肉
    </div>
    <div>
      <span>性别：</span>
      <input type="radio" name="" id="" value="男" v-model="gender"/>男
      <input type="radio" name="" id="" value="女" v-model="gender"/>女
    </div>
    <div>
      <span>自我介绍</span>
      <textarea v-model="intro"></textarea>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      from: "",
      hobby: [],
      gender:"男",
      intro:"",
    };
  },
};
</script>
```

### Vue指令-v-model（双向绑定）修饰符

语法：`v-model.修饰符="Vue数据变量"`

参数：

| 参数    | 说明                      |
| ------- | ------------------------- |
| .number | 以parsFloat转成数字类型   |
| .trim   | 去除首尾空白字符          |
| .lazy   | 在change时触发而非input时 |

```vue
<template>
  <div>
   <div>
     <span>年龄</span>
     <!-- 转换为parseFloat类型 尝试转-->
     <input type="number" v-model.number="age">
   </div>
   <div>
     <span>人生格言</span>
     <!-- 去除首尾两边空格 -->
     <input type="text" v-model.trim="motto">
   </div>
   <div>
     <span>个人简介</span>
     <!-- 在change时触发而非input时  只有失去焦点才会执行-->
     <textarea v-model.lazy="intro"></textarea>
   </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
     age:0,
     motto:"",
     intro:"",
    };
  },
};
</script>
```

### Vue指令-v-text和v-html

语法：

- v-text="Vue数据变量"
- v-html="Vue数据变量"

注意：会覆盖插值表达式{{}}

示例：

```vue
<template>
  <div>
   <p v-text="str"></p>
   <p v-html="str"></p>
   <p>{{10+20}}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
    str:"<span>Wosdas</span>",
    }
  }
};
</script>
```

### Vue指令-v-show和v-if的使用

作用：控制标签的隐藏或出现

语法：

- v-show="Vue变量"
- v-if="Vue变量"

区别：

- `v-show`：隐藏方式`display:none`
- `v-if`:采用从DOM树直接移除

```vue
<template>
  <div>
    <!-- v-show -->
    <h1 v-show="isShow">我是h1</h1>
    <h2 v-if="isOk">我是h2</h2>
    <p v-if="age >=18">成年了</p>
    <p v-else>未成年</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isShow:true,
      isOk:false,
      age:18,
    };
  },
};
</script>
```

### Vue指令-v-for

作用：可以遍历数组 / 对象 / 数字 / 字符串 (可遍历结构)

语法：

- v-for="(值变量，索引变量)in 目标结构"
- v-for="值变量 in 目标结构"

注意:  

- v-for的临时变量名不能用到v-for范围外
- 口诀: 让谁循环生成, v-for就写谁身上 

```vue
<template>
  <div>
    <ul>
      <!-- v-for="(值变量，索引变量)in 目标结构" -->
      <li v-for="(item ,index) in arr"
      :key="index">
        {{ item }} ----{{ index }}
      </li>
    </ul>
    <!-- v-for="值变量 in 目标结构" -->
    <ul>
      <li v-for="obj in stuArr" :key="obj.id">
        <span>{{ obj.name }}</span>
        <span>{{ obj.sex }}</span>
        <span>{{ obj.hobby }}</span>
      </li>
    </ul>
    <!-- v-for="(value,key) in 对象" -->
    <div>
      <p v-for="(value,key) in tObj" :key="value">
       <span> {{value}}</span>
       ======
       <span> {{ key }}</span>
      </p>
    </div>
    <!-- v-for="变量名 in 固定数字" -->
    <div v-for="n in count" :key="n">{{n}}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
       arr: ["小明", "小欢欢", "大黄"],
      stuArr: [
        {
          id: 1001,
          name: "孙悟空",
          sex: "男",
          hobby: "吃桃子",
        },
        {
          id: 1002,
          name: "猪八戒",
          sex: "男",
          hobby: "背媳妇",
        },
      ],
      tObj: {
        name: "小黑",
        age: 18,
        class: "1期",
      },
      count: 10,
    }
  },
  
}
</script>
```

