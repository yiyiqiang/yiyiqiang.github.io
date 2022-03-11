# 1. 【概述】

## 1.1. 【定义】

> * 基于对象和事件驱动的并且具有安全性能的解释型脚本语言
	
* **解释性**：不需要编译。浏览器直接解释执行
* **基于对象**：可直接使用 JS 已经创建的对象。如 Math、String
* **事件驱动**：可以对以事件驱动的方式响应客户端的输入，无须经过服务器端程序
* **安全性**：不允许访问本地硬盘，不能将数据写入服务器上
* **跨平台**：js 依赖于浏览器本身，与操作系统无关。浏览器是“宿主”，但 JS 的宿主不限于浏览器，也可能是服务器端，如服务器端 js 框架：node.js

## 1.2. 【发展历史】

<div alt="timeline">
    <div alt="timenode">
        <div alt="meta">1994年</div>
        <div alt="body">Netscape（网景）公司发布了 Navigator 浏览器1.0 版本</div>
    </div>
    <div alt="timenode">
        <div alt="meta">1995年</div>
        <div alt="body">发布了 JavaScript 语言</div>
    </div>
    <div alt="timenode">
        <div alt="meta">1996年</div>
        <div alt="body">
            <ol>
                <li>Js 在 Navigator 浏览器中开始使用</li>
                <li>微软发布 JScript 在 IE3.0 中使用</li>
                <li>网景公司将 JS 提交给 ECMA（欧洲计算机制造商协会）成为国际标准，用于对抗微软。由 ECMA 的第39号技术专家委员会负责制订 ECMAScript 标准，成员包括 Microsoft、Mozilla、Google 等大公司</li>
            </ol>
        </div>
    </div>
    <div alt="timenode">
        <div alt="meta">1997年</div>
        <div alt="body">
            <ul>
                <li>ECMA 推出浏览器标准语言 ECMAScript 1.0</li>
                <li>ECMAScript 是标准，而 Javascript，JScript，ActionScript 等脚本语言都是基于 ECMAScript 标准实现的</li>
            </ul>
        </div>
    </div>
    <div alt="timenode">
        <div alt="meta">2009年</div>
        <div alt="body">ECMAScript 5.0 发布</div>
    </div>
    <div alt="timenode">
        <div alt="meta">2011年</div>
        <div alt="body">ECMAScript5.1 发布，成为ISO国际标准，从而推动所有浏览器都支持</div>
    </div>
    <div alt="timenode">
        <div alt="meta">2015年 ~ 2020年</div>
        <div alt="body">
            <ul>
                <li>2015年 ECMAScript6 发布，更名为 ECMAScript 2015</li>
                <li>2016年 ECMAScript7 发布，ECMAScript2016</li>
                <li>2017年 ECMAScript8 发布，ECMAScript2017</li>
                <li>2018年 ECMAScript9 发布，ECMAScript2018</li>
                <li>2019年 ECMAScript10，ECMAScript2019</li>
                <li>2020年 ECMAScript11，ECMAScript2020</li>
                <li>...</li>
            </ul>
            <blockquote>从 2015年 开始 tc39 委员会决定每年发布新的 ECMAScript 版本</blockquote>
        </div>
    </div>
</div>

* 实际上 JavaScript 是由 ECMAScript，DOM 和 BOM 三者组成的
	1. **ECMAScript**：JavaScript 的语法标准 
	2. **DOM**：文档对象模型；JavaScript 操作网页上的元素的 API
	3. **BOM**：浏览器对象模型；JavaScript 操作浏览器的部分功能的 API

## 1.3. 【引用】

1. **行内式**
    * `<button onclick="alert('你好吗')"> 点击我 </button>`
    * `<button onclick="fun()"> 点击我 </button>`
    * `<a href="javascript:;"> 链接 </a>`

2. **内嵌式**
    * 格式：`<script>...</script>`
    * 可以使用多个，每一个之间都是有关联的
    * 网页是从上至下加载的，如果执行 js 代码时 HTML 还未被加载，那么 js 代码将无法添加交互（操作元素），同时，页面加载脚本会阻塞其他资源的下载，因此推荐将 script 标签放在 body 标签的底部
    
3. **外链式**
    * `<script src="*.js"></script>`
    * 由于每次加载外链式的 js 文件都会发送一次请求，这样非常消耗性能，所以在企业开发中推荐将多个 js 文件打包成为一个 js 文件，以提升网页的性能和加载速度

## 1.4. 【注释】

* **HTML**：`<!-- 注释的内容 -->`
* **CSS的注释**：`/* 注释的内容 */`
* **JavaScript**：`//单行注释` 、`/* 多行注释 */`

## 1.5. 【消息框】

* **警告框**：`alert(message)`
* **确认框**：`confirm(message)`  => 返回值：boolean
* **提示框**：`prompt([text][,defaultText])`
	* 单击取消按钮：null；单击确认按钮：则为输入文本
* **控制台显示消息的方式**
    * `console.log("Hello, JavaScript!");` 
    * `console.warn("警告输出！");`
    * `console.error("错误输出！");`
* **在页面中输出消息**
	* `document.write("大家好");`

# 2. 【变量和数据类型】

## 2.1. 【变量】

1. **命名法则**
	* **驼峰命名法**：从第二个单词开始首字母大写
	* **帕斯卡命名法**：单词首字母大写
	* **匈牙利命名法**：属性 + 类型 + 对象描述；eg：`G_Str_w3c`
2. **格式**：`var 变量名 = 数据;`
3. **注意事项**
	* 使用 `var` 关键字声明，可存储任意的数据类型数据
	* 变量数据类型是根据存储的值决定的，可以随时更改存储数据的类型
	* 定义了多个同名的变量时，后定义的同名变量会覆盖前面定义的同名变量
	* 声明变量的时候可以省略 `var` 关键字，但是不建议省略 
	* 不用 `var`，会污染全局变量；未使用 `var`，则这个变量就将被视为一个全局变量，如果脚本里以及存在一个与之同名的全局变量，这个函数会改变那个全局变量的值，首先在函数内部查找变量，找不到则到外层函数查找，逐步找到最外层，即 window 对象，并操作 window 对象的属性
	* 如果在对某个变量赋值之前未声明，赋值操作将自动声明该变量

4. **全局/局部变量**
	1. **全局变量**
		* 在函数外部声明的变量
		* 函数内部不使用 `var` 声明的变量（函数调用之后起作用）
	2. **局部变量** 
		* 函数内部声明的变量，变量前边有 `var` 关键字


## 2.2. 【数据类型】

1. **number**：小数与整数
	* 十进制表示法
	* 十六进制表示法：以 `0x` 开头
	* 八进制表示法：以 `0` 开头；ECMAScript 标准不支持；但 JavaScript 的某些实现支持
	
2. **string**：字符串，无字符概念
	* 单引号或双引号括起。若字符串含双引号，就用单引号括起，反之亦然
	* 若想用双引号括起一个本身就含双引号的字符串，就需要对双引号进行转义，反之亦然
	* 转义序列
		* `\xNN`：NN 是一个十六进制的数
		* `\uDDDD`：DDDD 是一个十六进制的数，表示一个 Unicode 字符
	
3. **boolean**：`true` 和 `false`
	
	* `false` 、 `0` 、 `null` 、 `undefined` 、 `NaN` 、`空字符串`：均为假
	
4. **undefined**：未定义，表示该变量声明了但未赋值

    * undefined 是 undefined 类型的字面量

    * undefined 值实际上是由 null 值衍生出来的，所以如果比较 undefined 和 null 是否相等，会返回true

5. **null**：代表对象不存在

    * null 类型只有一个值是 null
    * 使用 typeof 检查 null 会返回一个 object

6. **object**：对象类型

---

* **查看数据类型**：`console.log(typeof 100);`

# 3. 【】

