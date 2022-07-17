### 创建对象方法

#### 1.字面量

const obj ={

}

#### 2.new Object 创建对象

const obj =new Object

#### 3.构造函数

function Obj(name.age){

​	this.name=name

​	this.age=age

}

const Peiqi =new Obj('佩奇',6);

const Diaomao =new Obj('qwe',8)

#### 构造函数约定

大写字母命名

以new调用



使用new关键字调用函数的行为称作实例化

实例化构造函数没有参数时可以不用()  ..不推荐

无需return 返回值为新创建的对象

构造函数内部return无效



#### 实例化执行过程

function Pig(name, age, sex) {

   return {

   name: name,

   age: age,

   sex: sex

   }

  }

  let peiqi=Pig('佩奇',6,'男')

  // const peiqi =new Pig('佩奇',6,'男')

  console.log(peiqi);

创建新对象 

 构造函数this指向新对象 

 执行构造函数代码，修改this，添加新的属性 

返回新对象

#### 实例成员&静态成员

##### 实例成员

 实例对象的属性和方法即为实例成员

结构相同值不同的对象

构造函数创建的实例对象独立，不影响

##### 静态成员

构造函数的属性和方法被称为静态成员

公共属性或方法为静态成员

静态成员方法中的 this 指向构造函数本身

### 内置构造函数

#### Object

声明 obj为对象

Object.keys(obj)获取属性名(键) 返回数组

Object.values(obj)获取属性值 返回数组

Object.assign(接受源,拷贝源)拷贝 返回对象 可以用来合并对象

#### Array

forEach 遍历数组 不返回 不改原数组

filter 过滤 筛选 生成新数组

map 迭代数组 返回新数组 处理数据

reduce 累计器   reduce(和,每个值=>处理方法,初始值)

join 拼接字符串 join('以什么隔开')

find 查找元素 ，返回第一个元素

every 检查是否都符合条件 如果**所有元素**都通过检测返回 true，否则返回 false(重点)

some 检测数组中的元素是否满足指定条件   **如果数组中有**元素满足条件返回 true，否则返回 false

`concat`  合并两个数组，返回生成新数组

 `sort` 对原数组单元值排序

 `splice` 删除或替换原数组单元

`reverse` 反转数组

 `findIndex`  查找元素的索引值



伪数组变真

arr.from()



#### String

声明 str为字符串

str.lenght 长度

实例属性 `length` 用来获取字符串的度长(重点)

实例方法 `split('分隔符')` 用来将字符串拆分成数组(重点)

实例方法 `substring（需要截取的第一个字符的索引[,结束的索引号]）` 用于字符串截取(重点)

实例方法 `startsWith(检测字符串[, 检测位置索引号])` 检测是否以某字符开头(重点)

实例方法 `includes(搜索的字符串[, 检测位置索引号])` 判断一个字符串是否包含在另一个字符串中，根据情况返回 true 或 false(重点)

实例方法 `toUpperCase` 用于将字母转换成大写

实例方法 `toLowerCase` 用于将就转换成小写

实例方法 `indexOf`  检测是否包含某字符

实例方法 `endsWith` 检测是否以某字符结尾

实例方法 `replace` 用于替换字符串，支持正则匹配

实例方法 `match` 用于查找字符串，支持正则匹配

#### Number

实例方法 `toFixed` 用于设置保留小数位的长度