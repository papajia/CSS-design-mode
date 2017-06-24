# 你了解CSS设计模式吗？

## 前言（哆嗦话）

嘿，坐（作）前排（端）的同学！在普遍全套技能加身的你，是否有为可维护CSS烦恼过？是继承打补丁逐类复写，还是来套媒体查询大法，还是自己在造一套。ok，此时你后排的同学，或许也是这么想的。如果是这样我们不妨简单来了解下CSS设计模式，也许会让你眼前一亮。（老生常谈，众老司机请自觉 return；）

## 主题（上干货）
- BEM
- OOCSS
- SMACSS
- Atomic Design

#### BEM
BEM全称（block、element、modifier）是[Yandex](https://www.smashingmagazine.com/2012/04/a-new-front-end-methodology-bem/) 团队提出的CSS Class命名法.<br>
经典用例：
> .block { /* styles */ }  // 代表块
>
> .block__element { /* styles */ }  // 代表元素
>
> .block--modifier { /* styles */ }  // 代表修饰语

Block 块是一个独立实体，块可以是简单的或复合的。这里需要注意Block的含义，是独立块。块可以包含块。例如：
![Block](https://www.smashingmagazine.com/wp-content/uploads/2012/03/head-marked.png)
一个头部块，包含其他块。logo是独立块，menu是独立块。搜索及登陆都是独立块。

Element 元素是块的基础元素，是与块上下文相关的。通俗的讲就是对应的子元素。元素名称在块的范围内必须是唯一的。一个元素可重复多次使用。
![Element](https://www.smashingmagazine.com/wp-content/uploads/2012/03/input-button.jpg)<br>
input和button是搜索块的自元素。

Modifier 是描述Block和Element的属性、状态及外观。同一Block或Element可以有多个Modifier。

> &lt;ul class="menu menu_size_big menu_type_buttons" &gt;
>   ...
> &lt;/ul&gt;<br>
.menu_size_big {
  // CSS code to specify height
}<br>
.menu_type_buttons .menu__item {
  // CSS code to change item's look
}

BEM 优点 ：<br>
CSS 各块之间的优先级保持相对扁平。<br>
合理的块命名便于维护解读，让查找一目了然。<br>
能立即知道块下都有那些元素及元素状态。<br>
开发人员对CSS各块之间便于拓展维护。<br>
开发人员不用担心命名冲突等问题。<br>

#### OOCSS
OOCSS全称（Object Oriented CSS）由Nicole Sullivan提出的css理论,但更像一种约定规范：
- 减少对 HTML 结构依赖。（结构和主题分离。Separate structure and skin。）
- 增加 CSS 的 Class 重复使用。（容器和内容分离。Separate container and content。）

结构和主题分离：
> &lt;ul class="nav"&gt;<br>
> &lt;li&gt;<br>
> &lt;a href="#"&gt;首页&lt;/a&gt;<br>
> &lt;/li&gt;<br>
> &lt;/ui&gt;

CSS多为 ul.nav > li > a 逐级写。减少对结构的依赖，就是减少Dom结构层级、ul.nav a 或者给a加块元素名、行为类名 ul.nav a.nav-item。后者为OOCSS推荐。

容器和内容分离：
就像面向对象，抽离重复部分为对象。加强重复使用Class类。
> .btn {<br>
>   width: 100px;<br>
>   height: 100px;<br>
>   background-color: 999;<br>
>   &.btn-primary {<br>
>     background-color: yellow;<br>
>   }
> }

OOCSS 优点 ：<br>
与html结构结偶，减少对html结构依赖。<br>
提倡类名抽象，类高复用。<br>
减少代码量，缩减文件大小。<br>

#### SMACSS
SMACSS是Jonathan Snook的一个CSS框架。在SMACSS网站上，他表示，它更像是一个“风格指南”，而不是硬性的CSS框架。
规则重点分为五类：
- Base
- Layout
- Module
- State
- Theme

Base 用于默认值，如html，body，a，a：hover。
这包括CSS重置，并且通常在自己的基本CSS文件或主要CSS的开始。<br>

Layout 将页面分为具有页眉，页脚和文章等元素的部分。

Module 模块化元件。SMACSS文档将模块视为您的大多数元素。

State 用于每个元素的可能的变化（例如，活动，非活动，扩展，隐藏）。
这些以前缀，例如。
is-active，is-inactive，is-expanded，is-hidden或者通过伪类，例如：hover和：focus或media queries。

Theme 类似于状态，但是定义了模块和布局的外观。
它更适用于具有共同元素的较大网站，整个展示区域不同。
您可以在每页或每个部分的基础上添加主题变体。

#### Atomic Design
什么是原子设计?<br>
原子设计,原子原子顾名思义让我们联想到化学领域一切物质都是由原子所构成，原子结合构成分子。。。这就是原子设计的基本思想。
原子设计是创建设计系统的系统方法。分为5个层次：

>- 原子（Atoms）
>
- 分子（Molecules）
>
- 组织（Organisms）
>
- 模板（Templates）
>
- 页面（Pages）

![atoms](http://bradfrost.com/wp-content/uploads/2013/06/atomic-design.png)

Atoms
原子是物质的基本构成。应用于Web界面，原子是我们的HTML标签，例如表单标签，输入或按钮。
![atoms](http://bradfrost.com/wp-content/uploads/2013/06/atoms.jpg)

Molecules 分子是键合在一起的原子团，是化合物的最小基本单元。
比如，一个表单标签，输入框或者一个按钮单独的情况并不能完成一个用户功能，但是把它们组合在一起形成一个表单后，现在它们能共同完成一个任务比如搜索。
![Molecules](http://bradfrost.com/wp-content/uploads/2013/06/molecule.jpg)

Organisms 组织是由一组分子联合起来所形成的相对复杂，独立的界面功能块。
![Organisms](http://bradfrost.com/wp-content/uploads/2013/06/organism2.jpg)

Templates 模板主要由组装在一起形成页面的组织群组成。
![Templates](http://bradfrost.com/wp-content/uploads/2013/06/template1.jpg)

Pages 页面是模板的特定实例。
在这里，占位符内容被替换为真实的占位内容，以准确描述用户最终将看到什么。
![Pages](http://bradfrost.com/wp-content/uploads/2013/06/page1.jpg)

（题外话：这让我想起来乐高玩具。）
## 写在最后
头脑风暴了一圈，是不是感觉可以融汇贯通一下，没有绝对的模式，灵活运用就好。BEM的写法+OOCSS的理念也是一种方式。结合下乐高方式也不错。你的选择呢？

### 参考引用：
[BEM](https://www.smashingmagazine.com/2012/04/a-new-front-end-methodology-bem/)<br>
[OOCSS](https://github.com/stubbornella/oocss/wiki)<br>
[BEM SMACSS](https://www.sitepoint.com/bem-smacss-advice-from-developers/)<br>
[SMACSS](https://smacss.com/)<br>
[Atomic Design](http://bradfrost.com/blog/post/atomic-web-design/)
