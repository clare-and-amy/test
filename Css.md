# CSS

### grid
[阮一峰grid](https://www.ruanyifeng.com/blog/2019/03/grid-layout-tutorial.html)
默认item是block属性，但是当box加了justify-items，align-items，place-items（start，end，center，其中值为stretch：拉伸，占满单元格的整个宽度（默认值））
它的子元素就回变成inline-block属性, 标识子元素的位置

justify-content: start | end | center | stretch | space-around | space-between | space-evenly; 表示整个内容在容器的位置 
```
<style>
    .box1 {
        display: grid;
        grid-template-columns: 120px 80px 1fr;
        grid-template-rows: repeat(5, 60px);
        grid-gap: 10px;
        background-color: RED;
        padding: 10px;
    }
    .box1 .item {
        background-color: #FFFFFF;
        text-overflow: ellipsis;
        white-space: nowrap;
        overflow: hidden;
    }
</style>

<div class="box">
    <div class="box1">
        <div class="item">text-overflowtext-overflowtext-overflowtext-overflowtext-overflow</div>
        <div class="item">2</div>
        <div class="item">3</div>
        <div class="item">3</div>
        <div class="item">31</div>
    </div>
</div>
```
### flex
[阮一峰flex详解](https://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)
```
<style type="text/css">
    * {
        margin: 0;
    }
    #app {            
        display: flex;
        align-items: stretch;
        height: 100vh;
    }
    #left {
        width: 15%; 
        background: red;
    }
    #main {
        background: green;
        width: 100%;
        display: flex;
        flex-direction: column;
    }
    #header {
        background: white;
    }
    #content {
        flex-grow: 1;
    }
    #footer {
        align-self: flex-end;
        background: white;
        width: 100%;
    }
    ul li {
        list-style: none;
        float: left;
        line-height: 40px;
    }
</style>

<div id="app">
    <div id="left"></div>
    <div id="main">
        <div id="header">
            <ul>
                <li>xx</li>
                <li>xx</li>
                <li>xx</li>
            </ul>
        </div>
        <div id="content">
            11
        </div>
        <div id="footer">
            <div style="padding: 10px;">fdsafsda</div>
        </div>
    </div>
</div>
```