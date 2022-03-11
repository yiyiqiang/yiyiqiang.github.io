# 1. 【开山篇】

* HTML5 是 W3C 和 WHATWG 两个组织研发的
* HTML5 ≈ HTML + CSS + JavaScript 的集合

1. **简化 DTD 声明** `<!DOCTYPE html>`
2. **简化字符集声明**
    * 以前: `<meta http-equiv="Content-Type" content="text/html; charset=utf-8">`
    * 现在: `<meta charset="utf-8">`

# 2. 【新增标签】

## 2.1. 【网页多媒体】

1. **embed**：插入音频和视频

    ```html
    <embed src="media/music.mp3" width="400px" height="80px"/>
    <embed src="media/music.mp3" hidden="true" autostart="true" loop="true"/>
    <embed src="media/Apple.wmv" width="400px" height="80px"/>
    ```

2. **audio**：插入音频（ogg、mp3、wav）

    ```html
    <audio src="./source/audio.mp3" controls autoplay loop></audio>
    
    <audio controls>
    	<source src="./source/audio.mp3">
    	<source src="./source/audio.ogg">
    	<embed src="./source/audio.mp3" type="audio/mp3" width="300" height="100">
        对不起，您的浏览器不支持播放音频！请升级浏览器！
    </audio>
    ```

3. **video**：插入视频（ogg、mepg4、webm）

    ```html
    <video width="320" height="240" controls>
        <source src="movie.mp4" type="video/mp4">
        <source src="movie.ogg" type="video/ogg">
        <embed src="movie.mp4" type="video/mp4">
        您的浏览器不支持 video 标签。
    </video>
    ```

    * **API方法**

        1. 播放方法 `video.play();`
        2. 暂停方法 `video.pause();`
        3. 快进10秒 `video.currentTime+=10;`
        4. 是否静音 `video.muted=true/false;`
        5. 加速播放(3倍速度) `video.playbackRate=3;`
        6. 调高声音 `video.volume+=0.2;`

4. **track**：为诸如 `<video>` 和 `<audio>` 元素之类的媒介增加字幕

5. **canvas**：绘制图形

## 2.2. 【结构标签】

* `<header>` 标记定义一个页面或一个区域的头部

* `<main>` 页面主体内容，每个页面只包含一个 main 标签

* `<footer>` 标记定义一个页面或一个区域的底部

* `<nav>` 标记定义导航链接

* `<section>` 标记定义一个区域

* `<article>` 标记定义一篇文章

* `<aside>` 标记定义页面内容部分的侧边栏

* `<hgroup>` 对网页或区段的标题进行组合

    ```html
    <hgroup>
        <h1>回乡偶书二首</h1>
        <h2>其一</h2>
        <h2>贺知章<h2>
    </hgroup>
    ```

* `<figure>` 规定独立的流内容（图像、图表、照片、代码等等）

* `<figcaption>` 标签定义 figure 元素的标题

    ```html
    【图片+图注】
    <figure>
        <img src="images/coffee.jpg" alt="卡布奇诺" />
        <figcaption>卡布奇诺</figcaption>
    </figure>
    ```

* `<dialog>` 标记定义一个对话框

    ```html
    <dialog open>   <!-- open: 规定 dialog 元素是活动的，用户可与之交互 -->
        <dt>唐僧:悟空，你又调皮了，观音姐姐的月光宝盒怎么能乱扔呢？</dt>
        <dd>悟空:...(看着)</dd>
        <dt>唐僧:乱扔是不对的，砸到小朋友怎么办？就算砸不到小朋友，砸到花花草草也是不好的嘛</dt>
        <dd>悟空:...(纠结)</dd>
        <dt>唐僧:悟空你想要么？想要你就告诉我呀，你不告诉我怎么知道你想要呢？。。。。</dt>
        <dd>悟空:我靠!(一棍子抡上去！)</dd>
    </dialog>
    ```

    ---

    * **浏览器支持**

        1. **将元素定义为块元素**

            ```html
            header, section, footer, aside, nav, main, article, figure {
            	/* 让旧版本的浏览器正确显示这些元素 */
            	display: block;
            }
            ```

        2. **添加新元素**

            ```
            script:	document.createElement("myHero");   // 为 IE678 浏览器添加新的元素
            style:	myHero { display: block; background-color: #ddd; }
            html: 	<myHero>我的第一个新元素</myHero>
            ```

        3. **IE678 问题**

        	* 可以使用以上的方法来为 IE 浏览器添加 HTML5 元素
			
			* 针对IE678，html5shiv 是比较好的解决方案:
			
			    ```html
			    <!--[if lt IE 9]>
			    <script src="http://html5shiv.googlecode.com/svn/trunk/html5.js"></script>
			    <![endif]-->
			    
			    /*国内站点库*/
			    <!--[if lt IE 9]>
			    <script src="http://cdn.static.runoob.com/libs/html5shiv/3.7/html5shiv.min.js"></script>
			    <![endif]-->
			    ```

## 2.3. 【Web应用标签】

1. `<meter>`：状态标签（实时状态显示:气压、气温）

    ```html
    <meter value="3" min="0" max="10">十分之三</meter>
    <meter value="0.6">60%</meter>
    ```

2. `<progress>`：进度条（任务过程:安装、加载）
	
	```html
	<!-- 状态指示器 -->
	<progress></progress>
	
	<!-- 进度条默认最大值是1 -->
	<progress value="0.5" ></progress>
	<progress value="50" max="100" ></progress>
	```
	
3. `<datalist>`：数据列表，为 input 标记定义一个下拉列表，配合 option

    ```html
    <input type="text" list="input_list">
    <datalist id="input_list">
        <option value="雷军"></option>
        <option value="周鸿祎"></option>
    </datalist>
    ```

4. `<details>`：明细，定义元素的详细内容
	
	```html
	<details>
	    <summary>Copyright 2011.</summary>
	    <p>All pages and graphics on this web site are the property of W3School.</p>
	</details>
	```

## 2.4. 【注释标签】

* `<ruby>`：标记定义，注释或音标

* `<rp>`：告诉那些不支持 Ruby 元素的浏览器如何去显示

* `<rt>`：标记定义对ruby的注释内容文本

    ```html
    <ruby>
        汉 <rp>(</rp><rt>han</rt><rp>)</rp>
        字 <rp>(</rp><rt>zi</rt><rp>)</rp>
    </ruby>
    
    <ruby>
        明 日 <rp>(</rp><rt>ming ri</rt><rp>)</rp>
    </ruby>
    ```

## 2.5. 【mark 和 time】

* `<mark>`：标记突出显示的文本（黄色选中状态）
* `<time>`：日期/时间
* `<time datetime="2015-06-30">2015年6月30日</time>`
    * 标签中间的文本供人识别,例如 "今天"，"1小时前"，"结婚纪念日"，"情人节"等
    * datetime 属性值是一个固定格式的日期或时间值，可以被搜索引擎或屏幕阅读器识别
    * 若没定义 datetime 属性，则标签的文本内容需要是一个固定格式
    * **格式**：`2015-06-30` / `2015-06` / `15-06-30` / `14:54:39` / `14:54` / `2015-06-30 14:54:39`

# 3. 【表单】

1. **日期控件** `<input type="date" min="2010-08-14" max="2011-08-14" value="2010-08-14">`

1. **颜色控件** `<input type="color">`

1. **数字范围** `<input type="range" max="100" step="5" value="5">`

1. **时间控件** `<input type="time">`

1. **数字控件** `<input type="number" step="1" min="-5" max="10" value="0">`

1. **邮箱控件** `<input type="email" value="some@email.com">`

1. **网址控件** `<input type="url">`

1. **搜索控件** `<input type="search" results="10" placeholder="Search...">`

1. **电话控件** `<input type="tel" placeholder="(555) 555-5555" pattern="^\(?\d{3}\)?[-\s]\d{3}[-\s]\d{4}.*?$">`

1. **自定义提示信息**

    ```html
    <input id="text" pattern="^1[3-9]\d{9}$" required />
    
    text.oninvalid = function () {
        text.setCustomValidity("请不要输入火星的手机号好吗？");
    };
    ```

| **属性**         | **值**        | **含义**           |
| ---------------- | ------------- | -----------------|
| **placeholder**  | **提示文本**  | **提示信息，存在默认值将不显示** |
| **autofocus**    | **autofocus** | **当页面加载自动获得焦点**  |
| **multiple**     | **multiple**  | **多文件上传**   |
| **autocomplete** | **on / off**  | **自动提示功能**  |
| **required**     | **required**  | **必填项**       |

# 4. 【新增属性】

## 4.1. 【contenteditable 和 hidden】

* `Contenteditable`：把普通元素做成可以输入内容的元素
* `hidden`：隐藏元素

```html
<div class="box" contenteditable="true"></div>
<div class="box" hidden></div>
```

## 4.2. 【链接关系描述】

| 链接关系属性（rel） | 链接文件和当前文档之间的关系     |
| ------------------- | -------------------------------- |
| alternate           | 文档的可选版本                   |
| stylesheet          | 文档的外部样式表                 |
| shortcut icon       | 文档小图标                       |
| start               | 集合中的第一个文档               |
| next                | 集合中的下一个文档               |
| prev                | 集合中的前一个文档               |
| contents            | 文档目录                         |
| index               | 文档索引                         |
| glossary            | 文档中所用字词的术语表或解释     |
| copyright           | 包含版权信息的文档               |
| chapter             | 文档的章                         |
| section             | 文档的节                         |
| help                | 帮助文档                         |
| nofollow            | 指定 Google 搜索引擎不要跟踪链接 |
| licence             | 一般用于文献，表示许可证的含义   |
| tag                 | 标签集合                         |
| friend              | 友情链接                         |

## 4.3. 【ARIA】

> * 无障碍富互联网应用程序属性

# 5. 【SVG】

>  使用 XML 描述的矢量文件

浏览器直接打开

在HTML中使用 `<img>` 标签引用

直接在HTML中使用 SVG 标签

作为 CSS 背景

