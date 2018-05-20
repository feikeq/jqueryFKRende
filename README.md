# jqueryFKRende
## 肥客高性能数据绑定模板渲染引擎

### 绝大部份模板引擎或数据绑定框架都会指定特定的模板语言，这样会导至模板文件本身遭到破坏，无法直接预览页面本身的内容结构。
### 而我现在就是要解决这个问题，以模板文件为导向去制造数据结构，而不是以数据去构造模板逻辑。
* 1.不破坏原有模板结构
* 2.无须复杂的逻辑控制
* 3.自动循环遍历节点
* 4.高性能小体积
* 5.更加专注于业务


肥客联邦官网：
[http://fk68.net](http://fk68.net)

作者：肥客泉 - [https://github.com/feikeq/jqueryFKRende](https://github.com/feikeq/jqueryFKRende)



## 使用方法
### 1: 载入所需的文件
    ```html
    <!-- jQuery 公共资源库CDN -->
    <script src="http://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
    <!-- 引入肥客高性能数据绑定模板渲染引擎 JS 库文件 -->
    <script src="jqueryFKRende.min.js"></script>
    ```

### 2. 渲染指定模板内容
     ```javascript
     // 基于banner这个HTML元素指定其相应的JSON数据结构
     $("#banner").jqueryFKRende(json); 
     ```

### 3. 渲染指定模板内子元素内容
     ```javascript
     /*
       传入json对象 KEY就相当于对应的:
          HTML元素
          ID
          CLASS
          NAME
          为KEY的元素
        去做设置相应内容。
     */
     $("#banner").jqueryFKRende({h1:"标签、ID、CLASS、NAME、子元素"});
     ```


### 4. 设置模板及子元素属性
      ```javascript
      //程序会遍历利以上这些KEY，如果没有找到相对应的子元素，那就设置属性。
      $("#banner").jqueryFKRende({
        link:[
            "废客联邦",
            "提笔记",
            "CSGO战队"
            ]
      });
      ```

### 5. 既设置内容同时也设置属性
## 第4步中link对象其实可以把数组其实每一项当对象，它默认是都有KEY的，默认 0 1 2 没显示出来。
      ```javascript
      //所以这样是和上面那种是一样的，这样我们就可以同时设置属性和内容
      // link:["肥客联邦","提笔记","CSGO战队"]

      // link:[
      //  {0:"肥客联邦"},
      //  {1:"提笔记"},
      //  {1:"CSGO战队"}
      // ]

      $("#banner").jqueryFKRende({
        link:{href:"http://www.FK68.net",1:"废客联邦"},
            {href:"http://www.TiBiJi.com/",2:"提笔记"},
            {href:"http://cs.FK68.net/",0:"CSGO战队"}
      });
      ```




## 数据配置选项详解
**选择器**
指定模板渲染是在DOM中的哪个节点操作（必须）
```
  $("jq选择器").jqueryFKRende();
```

**JSON**
模板数据的JOSN对象{}内容（必须）
```
$("select").jqueryFKRende({JSON对象});
```


**KEY**
JOSN对象中的KEY（可选）
```
{KEY:val}
这里的KEY可以是 ：
HTML元素、HTML元素的ID、HTML元素的CLASS、HTML元素的NAME、也可以为val值
```


**VAL**
JOSN对象中的VAL（必须）
```
{key:VAL}
字符串文本、数字、数组、对象...等
```


**HTML元素属性**
对象的KEY就相当于对应的HTML元素或ID或CLASS或NAME为KEY的元素 如果都没有那就设置属性
```
{style:"background:#0ac2d2;"}
```

**HTML元素内容**
对象的KEY就相当于对应的HTML元素或ID或CLASS或NAME为KEY的元素 如果都没有那就设置属性
```
{b:"粗体显示"}
```


**循环例表**
只要对象或对象内有数组将自动在KEY所在节点内进行循环
```
a:[ "废客联邦","提笔记","CSGO战队"]
```




## 关于第5步在HTML5标准里自定义属性都是要加data前缀的。所以那些不按标准的排除在外。

## 案例中的HTML模板
```html
  <div id="banner" style="width: 100%; height: 200px; margin:0;padding:0;">
    <h1>标题1</h1>
    <div>
      <img name="pic" src="https://static.bootcss.com/www/assets/img/gruntjs.png" />
    </div>
    <h1 id="h2">标题<span>2</span></h1>
    <p>
      <a class="link" href="#" target="_blank">链接1</a>
      <a class="link" href="#" target="_blank">链接2</a>
      <a class="link" href="#" target="_blank">链接3</a>
      <a class="link" href="#" target="_blank">链接4</a>
    </p>
    <ul class="mypage">
      <li><i>#1</i><b> 内容11</b></li>
      <li><i>#2</i><b> 内容22</b></li>
      <li><i>#3</i><b> 内容33</b></li>
      <li><i>#4</i><b> 内容44</b></li>
      <li><i>#5</i><b> 内容55</b></li>
      <li><i>^6</i><b> 内容66</b></li>
    </ul>
  </div>
```



肥客联邦
自由无止境.自由的引领.自由的联盟.自由让你我腾飞!为了同一目标而奋斗，为了同一信念而聚一堂，为了网络事业的明天而烈火青春.
