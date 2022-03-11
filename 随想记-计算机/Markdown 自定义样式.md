# 1. 【有序、无序列表】

```css
li {
    list-style-type: none;
}

li:before {
    position: absolute;
    background: #81accf;
    color: #fff;
    cursor: pointer;
    -webkit-transition: all .3s ease-out;
    -moz-transition: all .3s ease-out;
    -o-transition: all .3s ease-out;
    -ms-transition: all .3s ease-out;
    transition: all .3s ease-out;
}

ol li:first-child {
    counter-reset: li;
}

li:hover:before {
    -webkit-transform:rotate(360deg);
    -moz-transform:rotate(360deg);
    -o-transform:rotate(360deg);
    -ms-transform:rotate(360deg);
    transform:rotate(360deg);
}

ol>li:before {
    margin-top: 2px;
    margin-left: -25px;
    width: 1.65em;
    height: 1.65em;
    border-radius: 0.825em;
    content: counter(li);
    counter-increment: li;
    text-align: center;
    font-size: .65em;
    line-height: 1.7em;
}

ul>li:before {
    margin-left: -22px;
    margin-top: 6px;
    width: .62em;
    height: .62em;
    border: .1em solid #81accf;
    border-radius: .31em;
    background: 0 0;
    content: '';
    line-height: .42em;
}

ul>li:hover:before {
    border-color: #ff5d52;
}

/* 列表子项上下间隔调整 */
li * {
    margin-top: 0;
    margin-bottom: 0;
}

/* 列表上下间隔调整 */
li {
    margin-top: 7px;
    margin-bottom: 7px; 
}
```

# 2. 【引用块】

```css
blockquote {
    padding: .5em 1em;
    margin: 12px 0;
    border-top-left-radius: 6px;
    border-bottom-left-radius: 6px;
    border-left: 5px solid #5fa7e4;
    background-color: #f4fcff;

}

blockquote > blockquote {
    border: 1px dashed rgba(95, 167, 228, .2);
    border-left: 5px solid #5fa7e4;
    margin-left: 2rem;
} 
```

# 3. 【标记】

```css
mark {
    display: inline;
    padding: .2em .6em;
    font-size: 90%;
    font-weight: 400;
    line-height: 1;
    color: #fff;
    text-align: center;
    white-space: nowrap;
    vertical-align: baseline;
    border-radius: .1rem;
    border-radius: 6px;
    background-color: #e91e64;
}
```

# 4. 【折叠标签】

```css
details {
    display: block;
    padding: 16px;
    margin: 1em 0;
    border-radius: 4px;
    background: #fff;
    font-size: 14px;
    -webkit-transition: all .28s ease;
    -moz-transition: all .28s ease;
    -o-transition: all .28s ease;
    -ms-transition: all .28s ease;
    transition: all .28s ease;
    -moz-transition: all .28s ease;
    -webkit-transition: all .28s ease;
    -o-transition: all .28s ease;
    border: 1px solid #f6f6f6;
}
summary {
    display: list-item;
}
details summary {
    cursor: pointer;
    padding: 16px;
    margin: -16px;
    border-radius: 4px;
    color: rgba(68,68,68,.7);
    font-size: .875rem!important;
    font-weight: 700;
    position: relative;
    line-height: normal;
}
details>summary {
    background: #ebf9ed;
}
details[open] {
    border-color: #00c4b6;
}
details[open]>summary {
    color: #444;
    margin-bottom: 0;
}
details[open]>summary {
    border-bottom: 1px solid #00c4b6;
    border-bottom-left-radius: 0;
    border-bottom-right-radius: 0;
}
```

# 5. 【时间轴】

```css
/* 时间轴（来自Volantis主题） */

div[alt="timeline"] {
    margin-top: 8px;
    margin-left: 8px;
}
div[alt="timenode"] {
    position: relative;
}
div[alt="timenode"]:after, div[alt="timenode"]:before {
    content: "";
    z-index: 1;
    position: absolute;
    background: rgba(68,215,182,.5);
    width: 2px;
    left: 7px;
}
div[alt="timenode"]:before {
    top: 0px;
    height: 6px;
}
div[alt="timenode"] div[alt="body"], div[alt="timenode"] div[alt="meta"] {
    max-width: calc(100% - 24px);
}
div[alt="timenode"] div[alt="meta"] {
    position: relative;
    color: #1f2d3d;
    line-height: 32px;
    font-size: .8rem;
    font-weight: 700;
    margin: 0 0 0 24px;
}
div[alt="timenode"] div[alt="meta"]:after, div[alt="timenode"] div[alt="meta"]:before {
    content: "";
    position: absolute;
    top: 8px;
    z-index: 2;
    left: -24px;
}
div[alt="timenode"] div[alt="meta"]:before {
    background: rgba(68,215,182,.5);
    width: 16px;
    height: 16px;
    border-radius: 8px;
}
div[alt="timenode"] div[alt="meta"]:after {
    background: #44d7b6;
    margin-left: 2px;
    margin-top: 2px;
    width: 12px;
    height: 12px;
    border-radius: 6px;
    -webkit-transform: scale(.5);
    -moz-transform: scale(.5);
    -o-transform: scale(.5);
    -ms-transform: scale(.5);
    transform: scale(.5);
}
div[alt="timenode"] div[alt="body"] {
    margin: 4px 0 10px 24px;
    padding: 10px;
    border-radius: 12px;
    background: #efeded;
    display: inline-block;
    font-size: .9rem;
}
div[alt="timenode"]:not(:last-child):after {
    top: 26px;
    height: calc(100% - 26px);
}
div[alt="timenode"]:last-child:after {
    top: 26px;
    height: calc(100% - 30px);
}
div[alt="timenode"]:hover div[alt="meta"]{
    color:#444;
}
div[alt="timenode"]:hover div[alt="meta"]:before{
    background:rgba(255,87,34,.5)
}
div[alt="timenode"]:hover div[alt="meta"]:after{
    background:#ff5722;-webkit-transform:scale(1);
    -moz-transform:scale(1);
    -o-transform:scale(1);
    -ms-transform:scale(1);
    transform:scale(1);
}
```