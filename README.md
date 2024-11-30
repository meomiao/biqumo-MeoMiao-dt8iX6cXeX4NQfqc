
## 前言：


因为 `JavaScript` 语言是一门极其松散、极其自由的语言，这意味着我们可以随心所欲的操作它，这是他的优点，但同时也是它的缺点。在编码过程中，我们需要一种良好的规范或者习惯来保持应用程序的一致性和可维护性。而今天我们要说的就是，怎么在日常编码中通过一些的良好的编码习惯，从你编码的基础层面就能使得你的 `JavaScript` 代码可以更好维护。


## 什么是可维护性？


很多人学习前端，可能是从各种不同的渠道获取学习资源，视频教学、看书等等，而每个人可能多多少少会有自己的一些编码习惯，当然如果是良好的习惯，我们就继续保持。可维护性的概念在我们整个开发流程中都适用，因为涉及内容太多，本文暂时只对 JavaScript 的可维护性进行说明。


## 什么是可维护性的代码？


可维护性的代码具备以下特点：


1. **容易理解**：我们在读一段代码时，能够很清楚的知道它是什么功能，需要什么数据，不管是自己重看还是别人来维护你的代码，都能轻松看懂；
2. **符合常识**：这点不太好定义，简单来说就是代码在需要的地方出现，不需要的地方不要出现，每个模块都能够实现自己该实现的功能，无论总体的操作是多么复杂；
3. **容易适配**：也就是代码具有通用性，思想接近我们了解的 [**工厂模式**](https://github.com)。我们不需要在数据发生改变时重新对方法进行处理，只需要在使用时传入我们的数据，然后返回我们需要的结果；
4. **容易扩展**：在代码的初始架构阶段，要有良好的设计，核心的功能要在未来能够支持扩展；
5. **容易调试**：在代码运行出现问题时，我们需要能够直观的看到报错，并能够准确定位出现问题的地方。这个有很多方式，大家感兴趣可以下去了解。


## 提高可维护性的编码规范


### 保持代码可读性


1. 保持代码可读性的首要条件是缩进。这个对于团队开发来说非常重要，在一个项目中保持一致的缩进能够极大程度上的提高代码的可读性。这里的缩进通常指我们的 `Tab` 键，一般来说是四个空格，这个需要看团队成员的编码习惯大家共同商议；
2. 时刻保持代码注释。这是最简单也是最多人容易忽略的地方，特别是项目长期有自己一个人负责维护，这时候我们就会觉得只要自己能看懂就行。然而最后我们自己写的方法甚至都需要反复确认才能知道具体功能。所以我们应该养成写注释的习惯，每个方法、关键变量以及关键逻辑都进行注释。以下是我们觉得必须写注释的地方：
	* 函数和方法
	* 完成同一任务的大型代码块
	* 使用了复杂算法的代码
	* 个性化的代码，一些必要但是只有我们能知道功能的代码“黑科技”


### 变量及函数规范命名


对变量和函数名保持规范命名，以达到见名知义，不要使用一些无意义的命名，比如：a、b、c、foo等。关于命名规范分为以下几点：


1. 变量名应该是符合意思的名词，比如 student；
2. 函数名通常以动词开始，使用小驼峰命名法，如果是获取 Boolean 值的函数，则以is开头使用小驼峰命名法；
3. 变量名和函数名如果表示的含义比较长也不用担心，只要符合含义并使用小驼峰命名即可；
4. 常量名全部大写，并且以下划线（`_`）拼接，例如 START\_TIME;
5. 名称在可能的情况尽量直观。


### 代码类型透明化


因为我们 JavaScript 对是非常松散类型的语言，对变量的类型并没有要求，所以很可能在使用过程中造成类型不匹配的错误。通过以下方式能够很好的避免：


1. 适当命名，变量命名要符合含义
2. 初始化变量时，表明变量类型
3. 写好注释


### 代码保持”松散耦合“


应用程序的某一部分对另一部分的依赖过于紧密，那么代码就会变得紧密耦合（高耦合），而我们编程界有一句流传甚广的至理名言：高内聚、低耦合，紧密耦合会导致我们的代码非常难以维护。


比较典型的问题就是在一个对象中引用另外一个对象，对象相互不独立。这导致一个对象有修改时还必须同时修改另一个。


所以我们要有松散耦合的意识，时刻注意不要让代码产生紧密耦合。


1. **解耦 HTML/JavaScript**


我在项目开发过程中，最常见的就是 HTML/JavaScript 耦合。这是因为它们之间要交互操作，需要通过不同的
方式将这两种技术联系起来。可惜的是，其中一些方式会导致 HTML 与 JavaScript 紧密耦合。


具体表现在：我们会在 JavaScript 代码中操作页面元素，也可能直接在 HTML 代码中添加 事件处理程序代码。这就导致我们每次修改 JavaScript 代码的同时可能还需要修改 HTML 代码。


那么我们应该怎么做呢？


* 尽量避免在 JavaScript 中创建大量的 HTML；
* HTML 渲染应该尽可能与 JavaScript 分开。


总的来说就是，解耦 HTML 和 JavaScript 可以节省排错时间，因为更容易定位错误来源。同样解耦也有助于保证可
维护性。修改行为只涉及 JavaScript，修改标记只涉及要渲染的文件。


2. **解耦 CSS/JavaScript**


Web应用的一个关键组成部分是 CSS，它主要承担着页面展示的职责。JavaScript 与 CSS 都是基于HTML构建的，因此它们常常被联合使用。就像 HTML 和 JavaScript 经常紧密结合一样，CSS 也可能与 JavaScript 形成紧密的耦合关系。


CSS 负责页面的样式显示，所以任何样式的问题都应该通过 CSS 文件解决：


那么当需要动态样式时，我们应该如何做呢？


* 通过修改元素的 CSS 类名，不要直接在 JavaScript 代码中修改样式；
* 保证层与层之间的适当分离。显示问题就只在 CSS 中去解决，保证跟 JavaScript无关。


3. **解耦应用程序逻辑/事件处理程序**
将应用程序逻辑与事件处理程序分开，各自负责处理各自的事情。事件处理程序应该。事件处理程序应该专注于 event 对象的相关信息，然后把这些信息传给处理应用程序逻辑的某些方法。


以下是在分离应用程序逻辑与业务逻辑时需要考虑的几个要点：


* 避免将整个 event 对象传递给其他函数，而应只传递 event 对象中的必要数据。
* 应确保应用程序中的每个操作都能够在没有事件处理器的情况下执行。
* 事件处理器应专注于处理事件本身，并将进一步的处理任务委托给应用程序逻辑。


遵守这些原则可以显著提高代码的可维护性，并为未来的测试和开发工作带来更多的灵活性。


#### 一些值得提倡的编码惯例


我们在工作中，通常是多人协作一个项目。这就意味着需要保持一致的规则，才能让我们的应用程序保持统一，不至于后期无法维护。这些都需要我们在在最初的时候约定好，并输出规范。


以下几点是我们在开发中值得提倡的一些惯例：


1. **尊重对象所有权**


JavaScript 的动态特性意味着几乎可以在任何时候修改任何东西。而在团队或者企业开发中，我们首先要做到的就是完全的尊重对象所有权。这意味着你只能修改属于你自己的对象，不要修改任何不属于你的对象，这里的修改包括：添加、修改、删除、重写，无论这个对象来自哪里。


具体一些就是：


* **不要给实例或原型添加属性。**
* **不要给实例或原型添加方法。**
* **不要重定义已有的方法。**


以上规则不仅适用于自定义类型和对象，而且适用于原生类型和对象，比如 Object、String、
document、window，等等。


但是有个问题是，我们有时候雀食需要在别人的对象基础上进项加工，功能可能大差不差，但是细微差别。这时我们可以按如下流程操作：


* 新建一个属于自己的对象；
* 通过新建的对象来与别人的对象交互；
* 创建新自定义类型继承本来想要修改的类型，可以给自定义类型添加新方法。


2. **不声明全局变量**


与尊重对象所有权密切相关的是尽可能不声明全局变量和函数。同样，这也关系到创建一致和可维护的脚本运行环境。最多可以创建一个全局变量，作为其他对象和函数的命名空间。


这就相当于我们创建一个属于自己的命名空间，所有需要使用到的变量都挂载在这个命名空间上，这样无论我们怎么修改，都不会影响到其他的变量，并且不会存在变量相互污染。


虽然命名空间需要多写一点代码，但从可维护性角度看，这个代价还是非常值得的。命名空间可以
确保代码与页面上的其他代码互不干扰。


3. **不要在逻辑判断中比较 null**
JavaScript 不会自动做任何类型检查，因此就需要开发者担起这个责任。很多 JavaScript 代码不会做类型检查。最常见的类型检查是看值是不是 null。


我们在判断或者比较时，最好直接判断确定的类型，比如是否是数组、是否存在对象上的某个值。


如果你的应用程序中有用到比较 null 的代码，可以尝试如下方式替换它：


* 如果值应该是引用类型，则使用 instanceof 操作符检查其构造函数。
* 如果值应该是原始类型，则使用 typeof 检查其类型。
* 如果希望值是有特定方法名的对象，则使用 typeof 操作符确保对象上存在给定名字的方法。


4. **使用常量**


对于某些多个地方使用到，并且可能存在修改的数据，我们应该把它保存为常量。这样我们就能统一管理，并且需要变更时只用更改一处，这保证了我们修改数据是不会引发错误。


以下是一些能保存为常量的数据：


* 以下是一些编程最佳实践，旨在提高代码的可维护性和适应性：
* **重复使用的值**：应将代码中多次出现的任何值定义为常量。这有助于避免因值在一个地方被修改而在另一个地方未被更新而导致的错误。这也适用于CSS中反复出现的类名。
* **用户界面文本**：所有向用户显示的文本都应集中管理，以便于支持多语言环境。
* **URL统一管理**：鉴于Web应用中资源路径（URL）可能发生变动，建议将所有URL集中在一处进行管理，便于后续的修改和维护。
* **潜在的变动值**：在代码中引入任何字面值时，应考虑其未来的变动可能性。如果存在变动的可能，最好将其提炼为常量。


**这些实践是企业级 JavaScript 开发中的常见做法，不仅可以使代码更加易于管理，还能防止因数据变化带来的潜在问题。**


## 写在后面


在本文中，我们探讨了确保代码可维护性的几个关键策略。代码的可维护性不仅关系到项目的长期成功，也直接影响开发团队的效率和工作满意度。


总的来说，投资于提高代码的可维护性将为企业带来长远的利益，包括降低成本、提高效率和增强产品质量。维护良好的代码库是任何成功软件项目的基石。


可维护性也是保证我们后续开发效率的一个重要因素，我们能够更加规范地去迭代和开发，减少新人员介入项目是的理解成本。


最后：喜欢本文的话请留下一个您的免费点赞和收藏吧！


感恩\~ Peace and love\~


 本博客参考[豆荚加速器](https://yirou.org)。转载请注明出处！
