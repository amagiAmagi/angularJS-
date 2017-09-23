

# 第一天MVC设计模式

## Angular简介

### Angular的简要历史

- Angular简称NG
- Angular最初诞生于2009年,由`Misko Hevery`等人创建.
- 由于Misko Hevery之前是做Java后台开发.
- 所以,在这个框架中融入了许多后台编程的思想在其中
- 比如:MVC设计模式、数据绑定等等.
- 后来,该框架被Google看中,Google将其收购.现在被Google所维护.

### Angular的重要特性.

- MVC: 在前端引入了MVC的设计模式.
- 模块化开发
- 自动的双向数据绑定
- 语义化标签(自定义标签)
- 依赖注入
- 其核心就是通过指令扩展了HTML,通过表达式绑定数据到HTML
- Angular不推崇DOM操作,也就是说在NG中几乎找不到任何的DOM操作.
- ng最主要是用来实现spa应用. - 单页面应用程序

### Angular的版本疑惑

- 目前Angular的版本有如下三种
- 1.x 比较稳定的版本,也是目前(2017.6)企业中的主流版本. 17年3月发布的1.6.4是1.x版本中最新的版本.
- 2.x 实际上从15年年底的时候,就发布了第一个alpha版本.直到16年9月才发布2.0的稳定版,其相对1.x版本做了很大的改动. 没有受到开发者的热烈追捧.
- 4.x 在2.x版本的ng遭受到失败后,Google立即启动了下1个版本的开发,由于新开发的版本做了相当多的改进和更新,所以下1个版本直接跳过3.0,叫做4.0, 并且第1个4.0的正式版已经于2017年的3月份发布. 然而,另外一个新的渐进式js框架-vue.js(中国人开发)正在挑战Angular的地位，而新的Angular版本是否能受到企业的青睐，让我们请时间做见证.
- 目前，尤其国内企业如果使用到了Angular,几乎绝大多数使用的仍然是1.x版本的Angular,因为1.x版本深受企业的认可,这也就是为什么直到4.0都发布了，Google还在维护1.x版本的原因. Google自己都不放弃1.x, 那么当然已经使用1.x的用户自然也不会放弃了.
- 版本历史参考 -> [点击链接](https://code.angularjs.org/)

## Angular初体验

### Angular下载

- 官网下载 [https://angularjs.org/](https://angularjs.org/)
- npm下载 `npm install angular`
- 通过bower下载 `bower install angular`

### Angular体验

+ 要实现的效果: 准备1个文本输入框,再准备1个h1标签.要求h1标签的文本和文本框的文字保持实时同步

+ 使用原生js实现

  - 监听文本框的keyUp事件.
  - 一旦触发该事件.
  - 取出文本框中的文本设置给h1标签的innerText.
  - 代码略过.

+ 使用Angular实现.

  - 第一步：引入Angular

    ```
      <script src="lib/angular.js"></script>

    ```

  - 第二步: 指定ng管理的标签.为body标签写上ng-app属性.代表body标签被ng管理.

    ```
      <body ng-app>
          <input type="text" name="" id="" ng-model="val">
          <h1>｛｛val｝｝</h1>
      </body>

    ```

  - 第三部: 数据绑定. 将文本框的数据和h1的数据进行绑定.

## MVC 设计模式

### 现实生活中的MVC

- 现实生活中的分工合作案例 -- 大饭店
  - 采购：负责原材料采购.
  - 小工: 打杂,洗菜,洗碗.
  - 厨师: 切菜 炒菜
  - 服务员：端菜 迎宾
  - 收银员: 收钱.
  - 店长: 指挥协调其它人员工作.
- 在一些街边小饭馆其实这些事情完全是交给一个人去做 --> 老板
  - 所有的事情都是这1个人去做.
- 对比一下这两种经营方式的区别
  - 大饭店: 正规,分工合作,各司其职,效率高.
  - 小饭馆: 不正规,慌乱.效率低下.
- 同样的事情两种实现方式
  - 都是将客人点的菜展示到餐桌上.
  - 不同的单位使用了不同的流程.
  - 大饭店: 每个人负责1个流程.高效并且可维护程度极高. 挂了1个人,不影响其它人.只换这1个人就可以.
  - 小饭馆: 1个人负责整个流程,效率低下并且可维护程度极低,老板挂了,饭馆就得关门.
- 由此可见,分工是多么的重要

### 代码中的MVC

- 实际上,我们写网站的过程,和开饭店的原理和流程极其相似,我们写网站是将数据展示到页面上.
- 目前,我们写代码都是一股脑的将所有的代码写在一起,这样去写固然没有什么问题，因为你终究还是将效果实现了.
- 但是这样做的后果是可怕的,随着项目越来越大,你的代码将变得非常难以维护.
- 为了让我们的代码更加容易的维护,也为了使得我们的代码层次更加分明
- 我们将我们的代码分为三部分
  - M - Model 数据 数据实体,用来保存页面要展示的数据.
  - V - View 视图 负责显示数据的,一般其实就是指的html页面.
  - C - Controller 控制器 控制整个业务逻辑,负责处理数据,比如数据的获取,以及数据的过滤，进而影响数据在视图上的展示.
- 这样,这3部分各司其职,分工合作,我们的代码就会变得更有层次并容易维护.
- 这样的程序设计模式,我们就叫做MVC设计模式.
- 所以,MVC并不是一个新的知识点,而是一个新的写代码的套路.MVC是由后端而来,由于受到前端技术的限制便有了一些细节的调整，进而出现了很多MVC的衍生版（子集）如MVVM、MVW、MVP、MV*等。
- `注：做为初学可以不必过于在意这些概念。`

## 模块化

- 使用AngularJS构建应用（App）时是以模块化（Module）的方式组织的，即将整个应用划分成若干模块，每个模块都有各自的职责，最终组合成一个整体。
- 采用模块化的组织方式，可以最大程度的实现代码的复用，可以像搭积木一样进行开发。

### 定义应用

+ 通过为任一HTML标签添加ng-app属性，可以指定一个应用，表示此标签所包裹的内容都属于应用（App）的一部分。通俗的理解就是: ng-app属性标签被Angular管理，包括其中的子标签.Angular会认为这是一个应用，将其作为一个应用来看待。

### 定义模块

+ AngularJS提供了一个全局对象angular,调用该全局对象的module()方法可以创建一个模块.该方法返回一个模块对象.这个模块对象就是AngularJS用来管理应用的对象.

```
  <!DOCTYPE html>
  <!--为html标签定义ng-app属性 代表整个文档都被ng管理-->
  <html lang="en" ng-app="myApp">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
      <script src="lib/angular.js"></script>
  </head>
  <body>

  <script>
      //调用全局对象angular的module方法创建一个模块.
      //第一个参数: 模块要管理的标签范围,写上ng-app属性的值.
      //第二个参数: 模块依赖,数组,如果不需要依赖,就直接写一个空数组就可以.
      //返回值:返回的app对象,我们可以认为这个对象就是用来管理这个模块的.
      var app = angular.module('myApp',[])
  </script>
  </body>
  </html>
```

### 定义控制器

- 接下来我们可以通过app模块对象来创建控制器.

- 调用app模块对象的controller方法，就可以创建控制器.

  ```
    //调用全局对象angular的module方法创建一个模块.
    //第一个参数: 模块要管理的标签范围,写上ng-app属性的值.
    //第二个参数: 模块依赖,数组,如果不需要依赖,就直接写一个空数组就可以.
    //返回值:返回的app对象,我们可以认为这个对象就是ng用来管理这个模块的.
    var app = angular.module('myApp',[])

    //调用app的controller方法创建控制器.
    //第一个参数: 要将创建的控制器关联到指定的View上，字符串.
    //第二个参数: 这是一个数组,数组的其中一个元素是'$scope',
    //           数组的最后一个元素必须是1个function 参数是$scope
    //           先这么认为,就这么死写,后面会解释原因.
    app.controller('demoCtrl',['$scope',function ($scope) {

    }]);

  ```

- 但是这个时候,我们只是创建了控制器,并没有将控制器和视图关联起来.

- 视图是用来负责显示数据的,控制器是来处理数据模型,并将数据模型给视图展示.

- 视图就是我们的html页面. 所以我们可以指定1个html元素(视图)与这个控制器相关联.

- 为这个html元素指定1个ng-controller属性.值为创建controller的第1个参数的值.

  ```
    <div ng-controller="demoCtrl"> <!-- 这个时候,创建的控制器，就与这个视图关联起来了. -->
        <dl>
            <dt></dt>
            <dd></dd>
        </dl>
    </div>

  ```

- 这个时候,创建的控制器，就与这个视图关联起来了

- 在控制器中就可以处理制造数据.视图中就可以显示模型数据了.

### 数据模型

- 控制器负责处理制造模型数据.

- 视图负责显示控制器制造的模型数据.

- 那么控制器如何制造数据呢?

  ```
    app.controller('demoCtrl',['$scope',function ($scope) {
    //我们可以认为,$scope就是一个数据模型.
    //这是一个对象，
    //这个对象可以在控制器中访问,也可以在与控制器关联的视图中直接访问.
    //那么这个时候,控制器中可以将制造的数据放在这个$scope对象中.
    $scope.name = '小明';
    $scope.info = '我在学习前端开发';
    }]);
  ```

- 这个时候,控制器已经负责将数据模型构建完毕,那么视图中如何展示这些数据呢?![img](images/331.png)

- 最后,视图中就显示出来数据了.

## Angular基本结构

- 1.指定Angular管理的范围.`ng-app`
- 2.创建模块. `angular.module()`
- 3.创建角色
  - 3.1创建控制器 `app.controller()`
  - 3.2指定与控制器关联的视图 `ng-controller`
- 4.控制器制造数据模型并附到$scope. `$scope.xx = yy;`
- 5.在视图中显示模型数据. `｛｛xx｝｝`

```
<!DOCTYPE html>
<!-- 1.指定整个html文档都被ng管理-->
<html lang="en" ng-app="hmApp">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="lib/angular.js"></script>

</head>
<body>
    <!-- 将视图与控制器相关联 -->
    <table ng-controller="stuList">
        <tr>
            <td>编号</td>
            <td>姓名</td>
            <td>性别</td>
            <td>年龄</td>
        </tr>
        <tr ng-repeat="stu in students"><!-- 遍历数组,并循环生成html -->
            <td>｛｛stu.id}}</td>
            <td>｛｛stu.name}}</td>
            <td>｛｛stu.gender}}</td>
            <td>｛｛stu.age}}</td>
        </tr>
    </table>
<script>
    //2.创建模块
    var app = angular.module('hmApp',[]);
    //3.创建MVC角色. 控制器,视图
    app.controller('stuList',['$scope',function ($scope) {
        //制造数据模型,并绑定到$scope中.
        $scope.students = [
            {id:1,name:'小明',gender:'男',age:18},
            {id:2,name:'小花',gender:'女',age:16},
            {id:3,name:'小强',gender:'男',age:14},
            {id:4,name:'小东',gender:'男',age:19},
            {id:5,name:'小常',gender:'女',age:20}
        ];
    }]);
</script>
</body>
</html>

```

## Angular指令

- HTML在构建应用（App）时存在诸多不足之处
- AngularJS通过扩展一系列的HTML属性或标签来弥补这些缺陷
- 所谓指令就是AngularJS自定义的HTML属性或标签
- 这些指令都是以ng-做为前缀的，例如ng-app、ng-controller、ng-repeat等。

### 内置指令

- `ng-app` 指定应用根元素 也就是ng管理的范围.可以使用全局对象angular的module方法根据该属性的值创建模块对象.
- `ng-controller` 指定与控制器关联的视图.
- `ng-show` 控制元素及其子元素是否显示 true->显示 false->不显示
- `ng-hide` 控制元素及其子元素是否隐藏 true->隐藏 false->不隐藏
- `ng-if` 控制元素及其子元素是否创建 true->创建 false->删除.
- `ng-src` 增强图片路径. src=""虽然能显示,但是会报错.报错的原因.
- `ng-href` 增强href路径
- `ng-class` 值为对象 `{red:true}` 表示会添加1个red类名到元素身上.`{red:false}`不会将red类名添加到元素身上.
- `ng-include` 将外部文件包含进来.一般用在页面的公共部分.被请求的页面是以ajax的方式请求的. `ng-inlcude="'path'"`需要注意的是,给该属性赋值的时候,属性本身的值应该使用双引号引起来,但是其中的路径还要使用单引号引起来.
- `ng-disable` 是否禁用表单元素
- `ng-readonly` 是否只读
- `ng-checked`　原生的checked属性带有歧义,ng补充1个新的指令ng-checked 其值bool类型 true选中 false不选中.
- `ng-selected` 是否选中
- 后续的学习中我们还会介绍其他的内置指令.

### 自定义指令

- AngularJS不仅提供了功能强大的内置指令.还提供了一套允许我们自定义指令的机制.

- 如果我们觉得ng提供的指令不够强大和好用,我们完全可以定义我们自己的指令.

- 模块对象app,提供了一个`directive`方法,这个方法就可以让我们自定义指令.

- 该方法需要两个参数

  - 第1个参数 指令的名称 - 指令名称不能包含符号，如果指令名称是`tag`,那么直接使用tag就行. 如果指令是`hmTag`,那么要使用`hm-tag`

  - 第2个参数 回调函数

    - 在ng解析这个指令的时候,就会自动去执行这个回调函数.
    - 这个回调函数必须要按照要求返回1个对象.
      - restrict: ECMA E:Element C:Class M:Mark A:Attribute 自定义指令
      - replace: bool值,是否替换原有标签.
      - template: 模板,自定义指令将被替换成什么.
      - templateUrl:加载外部文件 给一个需要加载的文件的路径.

    ```
    <!DOCTYPE html>
    <html lang="en" ng-app="hmApp">
    <head>
      <meta charset="UTF-8">
      <title>Title</title>
      <script src="lib/angular.js"></script>
    </head>
    <body>
    <div hm-tag></div> <!--加了这个自定义指令的标签中,就会被自动渲染自定义指令对应的template -->
    <script>
      var app = angular.module('hmApp',[]);
      app.directive('hmTag',function () {
          return {
              restrict:'EA',
              replace:false,
              template:'<h1>我是中国人,我爱自己的祖国</h1>'
          };
      });
    </script>
    </body>
    </html>
    ```

## 数据单向绑定

### 数据单向绑定

- 所谓的数据的单向绑定,指的就是在控制器中制造数据模型，并将数据模型显示在视图上的过程.

- 处理方式其实我们前面也完全学习过了.

- 数据单向绑定的步骤

  - 1.先在控制器中制造数据.

  - 2.在视图中使用绑定符号｛｛｝｝ 将控制器制造的数据模型显示.

    ```
    <!DOCTYPE html>
    <html lang="en" ng-app="hmApp">
    <head>
      <meta charset="UTF-8">
      <title>Title</title>
      <script src="lib/angular.js"></script>
    </head>
    <body>
    <div ng-controller="demoCtrl">
      <h1></h1>
      <ul>
          <li ng-repeat="item in data.courses"></li>
      </ul>
    </div>
    <script>
      var app = angular.module('hmApp',[]);
      app.controller('demoCtrl',['$scope',function ($scope) {
          $scope.data = {
              name:"小明",
              courses:['html','css','js']
          };
      }]);
    </script>
    </body>
    </html>

    ```

- 需要特别说明的是`ng-bind`指令和`｛｛｝｝`符号的效果是一样的.

- `｛｛｝｝`符号是`ng-bind`指令的简写形式.

- 所以,上面的代码也可以这样写.

  ```
    <div ng-controller="demoCtrl">
        <h1 ng-bind="data.name"></h1>
        <!-- ng-bind指令与｛｛｝｝符号完全等价 -->
        <ul>
            <li ng-repeat="item in data.courses" ng-bind="item"></li>
        </ul>
    </div>

  ```

- 虽然`ng-bind`与`｛｛｝｝`使用效果是一样的，但是在更多的地方我们仍然使用`｛｛｝｝`的场景更多一些

- 比如: 这样的情况使用`｛｛｝｝`就方便的很多了.`  大家好,我叫｛｛name｝｝,我今年岁｛｛age｝｝了`

### 解决闪烁问题

- 虽然`｛｛｝｝`符号和`ng-bind`指令作用是一样的.但是他们在效果上有一些些区别
- 使用`｛｛｝｝`符号有可能会出现闪烁现行(当吧ng文件的引入放在页面后面的时候)
- 出现闪烁的原因
  - 浏览器先渲染html页面.遇到ng指令不认识 原因输出.
  - 而后,ng开始工作,渲染绑定数据.
  - 所以，中间有这么一个闪烁的过程.
- 解决闪烁问题
  - 第一种方式: 将ng文件的引入放在head标签中.
  - 第二种方式: 为标签添加1个`ng-cloak`指令.就可以解决.
- `ng-cloak`的原理.ng会自动的生成1段css代码,将这个标签隐藏.当数据绑定工作完成之后,再显示这个标签.

## 数据双向绑定

- `ng-model`指令可以作用于表单元素.

- 该指令的作用

  - 声明1个变量.该属性的值就是声明的变量.
  - 这个变量的值和表单元素的值是相互影响的.
  - 表单元素的值发生变化,这个变量的值也会跟着发生变化.
  - 这个变量的值发生变化,表单元素的值也会跟着发生变化.

- 这样的数据绑定,就叫做双向数据绑定.

  ```
    <body>
        <div ng-controller="demoCtrl">
            <input type="text" ng-model="val"> <!-- 使用ng-model指令声明的变量val，
            被文本框的值绑定 文本框的值改变会影响val的值,val的值得改变也会影响文本框的值, 
            这个时候，文本框的值和变量val是一个双向绑定的关系.-->
            <h1>｛｛val}}</h1>
            <button ng-click="show()">按钮</button> <!-- 按钮点击的时候,
            执行控制器绑定在$scope上的show方法，这个方法中直接修改了val
            变量的值, 你会发现文本框中的数据也会跟着一起改变.
            这就是双向数据绑定-->
        </div>
        <script>
            var app = angular.module('hmApp',[]);
            app.controller('demoCtrl',['$scope',function ($scope) {
                $scope.show = function () {
                    $scope.val = 199;
                }
            }]);
        </script>
    </body>
  ```

## ng-init指令

- 数据模型的初始化,我们一般是放在控制器中.

- 为$scope对象附加属性的方式来追加.

- 然后在视图中就可以直接绑定数据.

- 实际上,Angular还提供了一种更为简便的方式来初始化模型数据.就是使用`ng-init`属性.

- 使用ng-init初始化的变量在控制器中通过$scope仍然可以访问

  ```
    <div ng-init="name='jack';age=10"> <!-- 初始化多个变量的话中间使用分号隔开 -->
        ｛｛name}}
        ｛｛age}}
    </div>
    <script>
        var app = angular.module('hmApp',[]);
    </script>

  ```

- 对于一些复杂的数据模型,比如数组、对象明显在controller中初始化就方便的很多.

## Angular事件处理

### ng-click

- 原生js中如果需要绑定点击事件,在html元素中使用`onclick`属性,指定该属性的值为一个函数调用.

- 那么这个函数就是全局的函数,会造成全局污染.

  ```
    <script>
        function login(){
            .......
        }
    </script>
    <button onclick="login()">登录</button>

  ```

- Angular为了解决这个问题,使用了1个ng指令`ng-click`

- 这是Angular中的点击指令,为其赋值一个函数,不同的是,这个函数需要在控制器中绑定到$scope对象中.

- 那么这个函数就不再是一个全局的函数,就不存在全局污染的问题了.

  ```
    <div ng-controller="demoCtrl">
        <!-- 指定按钮的ng-click为login-->
        <button ng-click="login()">按钮</button>
    </div>
    <script>
        var app = angular.module('hmApp',[]);
        app.controller('demoCtrl',['$scope',function ($scope) {
            //在控制器中为$scope绑定login函数.这样在视图中就可以调用
            $scope.login = function () { 
                alert("正在登录,请稍后.....");
            }
        }]);
    </script>
  ```

### ng-mouseover

+ 其实原理是一样的,这是ng的指令 用来绑定鼠标移入事件.`  

​      按钮
​      

​      var app = angular.module('hmApp',[]);
​      app.controller('demoCtrl',['$scope',function ($scope) {
​          $scope.login = function () {
​              alert("正在登录,请稍后.....");
​          };
​          $scope.mover = function () {
​              console.log("鼠标移入了.....");
​          }
​      }]);

### 其它事件指令

- 其实你应该已经猜测到一些规律了.
- Angular的事件指令是在原生指令属性的基础之上把on去掉替换为ng-
- onclick --> ng-click
- onmouseover --> ng-mouseover
- onkeyup --> ng-keyup
- ......

## 数据处理

### ng-repeat指令

- 用于循环生成标签,并绑定数据.

- 可以遍历数组.

  ```
    <!DOCTYPE html>
    <html lang="en" ng-app="hmApp">
    <head>
        <meta charset="UTF-8">
        <title>Title</title>
        <script src="lib/angular.min.js"></script>
    </head>
    <body>
        <div ng-controller="processDataView">
            <ul>
                <!-- ng-repeat指令代表重复生成这个标签.值代表遍历数组中的每一个元素 并绑定显示 -->
                <li ng-repeat="item in lessons">｛｛item}}</li>
            </ul>
        </div>
        <script>
            var app = angular.module('hmApp',[]);
            app.controller('processDataView',['$scope',function ($scope) {
                $scope.lessons = ['html','css','js','jQuery'];
            }])
        </script>
    </body>
    </html>

  ```

- 可以遍历对象

  ```
    <!DOCTYPE html>
    <html lang="en" ng-app="hmApp">
    <head>
        <meta charset="UTF-8">
        <title>Title</title>
        <script src="lib/angular.min.js"></script>
    </head>
    <body>
        <div ng-controller="processDataView">
            <ul>
                <li ng-repeat="item in lessons"></li>
            </ul>
            <table>
                <tr>
                    <!--遍历对象,item迭代变量直接就是每一个属性的值-->
                    <td ng-repeat="item in student">｛｛item}}</td>
                    <!--如果希望得到属性名称和属性值 可以像下面这样
                        如果是数组,key拿到的就是下标          -->
                    <td ng-repeat="(key,item) in student">｛｛key}}:｛｛item}}</td>
                </tr>
            </table>
        </div>
        <script>
            var app = angular.module('hmApp',[]);
            app.controller('processDataView',['$scope',function ($scope) {
                $scope.lessons = ['html','css','js','jQuery'];
                $scope.student = {
                    name:"杰克",
                    age:18,
                    gender:"男"
                };
            }])
        </script>
    </body>
    </html>
  ```

### ng-switch

- 该指令的作用与js的`switch-case`非常相像

- 判断变量的值,如果变量的之与列出的任意1个值相等,则执行其中的逻辑.

- 语法规则

  ```
    <!-- 判断变量item的值 可以直接简写为ng-switch -->
    <li ng-repeat="item in list" ng-switch on="item">
        <span ng-switch-when="html">我喜欢html</span>
        <p ng-switch-when="ccs">哈哈css</p>
        <a ng-switch-when="js" href="#">哦js</a>
        <span ng-switch-when="jQuery">like jQuery</span>
        <span ng-switch-default>啦啦啦,没有匹配到</span>
    </li>
    <!-- 在重复li标签时 到底嵌套那1个 根据when的值匹配来决定 当没有任何匹配的时候 就是default-->

  ```

- 也可以下面这样使用

  ```
    <!DOCTYPE html>
    <html lang="en" ng-app="hmApp">
    <head>
        <meta charset="UTF-8">
        <title>Title</title>
        <script src="lib/angular.min.js"></script>
    </head>
    <body>
        <div ng-controller="demoCtrl" ng-switch="name">
            <div ng-switch-when="rose">Rose</div>
            <div ng-switch-when="jack">Jack</div>
            <div ng-switch-when="lily">Lily</div>
            <div ng-switch-when="poly">Poly</div>
            <div ng-switch-default>默认选项</div>
        </div>
    <script>
        var app = angular.module('hmApp',[]);
        app.controller('demoCtrl',['$scope',function ($scope) {
            $scope.name = "jack";
        }]);
    </script>
    </body>
    </html>
  ```

## Tabs案例

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Tab 标签</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background-color: #F7F7F7;
        }

        .tabs {
            width: 400px;
            margin: 30px auto;
            background-color: #FFF;
            border: 1px solid #C0DCC0;
            box-sizing: border-box;
        }

        .tabs nav {
            height: 40px;
            text-align: center;
            line-height: 40px;
            overflow: hidden;
            background-color: #C0DCC0;
            display: flex;
        }

        nav a {
            display: block;
            width: 100px;
            border-right: 1px solid #FFF;
            color: #000;
            text-decoration: none;
        }

        nav a:last-child {
            border-right: 0 none;
        }

        nav a.active {
            background-color: #9BAF9B;
        }

        .cont {
            overflow: hidden;
        }

        .cont ol {
            line-height: 30px;
        }

    </style>
    <script src="lib/angular.min.js"></script>
</head>
<body ng-app="hmApp">
    <div class="tabs" ng-controller="TabsCtrl">
        <nav>
            <a href="javascript:;" ng-click="switch('local')" ng-class="{active:flag=='local'}">国内新闻</a>
            <a href="javascript:;" ng-click="switch('global')" ng-class="{active:flag=='global'}">国际新闻</a>
            <a href="javascript:;" ng-click="switch('sport')" ng-class="{active:flag=='sport'}">体育新闻</a>
            <a href="javascript:;" ng-click="switch('funny')" ng-class="{active:flag=='funny'}">娱乐新闻</a>
        </nav>
        <!-- 判断key数据的值 -->
        <div ng-switch="flag">
            <!-- 当key值funny时 -->
            <section class="cont" ng-switch-when="local">
                <ol>
                    <li>河南再次发生矿难，死伤人数超砖石ddddddddddddd过100dddads</li>
                    <li>禽流感在全国物农延，温家宝指示</li>
                    <li>南方大旱，农作物减产绝收面积上亩</li>
                    <li>猪流感在广东群体性暴发</li>
                    <li>禽流感在全农作物继续蔓延，温家宝指示</li>
                    <li>猪流感在广东群体性暴发</li>
                </ol>
            </section>
            <!-- 当key值local时 -->
            <section class="cont" ng-switch-when="global">
                <ol>
                    <li>河感在生矿难，死伤在全10</li>
                    <li>禽流感在感在广1处继续蔓延，温家宝指示</li>
                    <li>南方大旱，农作物减产绝收面积上亩</li>
                    <li>猪流感在广在全国暴发</li>
                    <li>禽流感在全国多处继续蔓延，温家宝指示</li>
                    <li>南方大旱，农作物减产绝收面积上亩</li>
                    <li>猪流感在广东群体性暴发</li>
                </ol>
            </section>
            <!-- 当key值sports时 -->
            <section class="cont" ng-switch-when="sport">
                <ol>
                    <li>河南再次发生矿难，死伤人数超过100</li>
                    <li>禽流感在全国多处农作物农延，温家宝指示</li>
                    <li>南方大旱，农作物减产绝收面积上亩</li>
                    <li>猪流感在广东群体性暴发</li>
                    <li>禽流感在全农作物继续蔓延，温家宝指示</li>
                    <li>南方大农作物减产绝收面积上亩</li>
                    <li>猪流感在广东群体性暴发</li>
                </ol>
            </section>
            <!-- 当key值global时 -->
            <section class="cont" ng-switch-when="funny">
                <ol>
                    <li>河南再次发生矿难，死伤人数超过100</li>
                    <li>禽流感次发生蔓延，温家宝指示</li>
                    <li>南方大旱，农作物减产绝收面积上亩</li>
                    <li>猪流感在广减产绝收发</li>
                    <li>禽流感在全国多作物减产绝收面积上亩</li>
                    <li>猪流感在广东群体性暴发</li>
                </ol>
            </section>
        </div>
    </div>
    <script>
        var app = angular.module('hmApp',[]);
        app.controller('TabsCtrl',['$scope',function ($scope) {
            $scope.flag = 'local';
            $scope.switch = function (key) {
                $scope.flag = key;
            }
        }]);
    </script>
</body>
</html>
```

# 依赖注入服务

## Angular作用域

- 1.相互独立的视图/控制器，他们的作用域($scope)也是相互独立,互不影响的.

  ```
    <!DOCTYPE html>
    <html lang="en" ng-app="hmApp">
    <head>
        <meta charset="UTF-8">
        <title>Title</title>
        <script src="lib/angular.min.js"></script>
    </head>
    <body>
        <div ng-controller="demoCtrl1"></div>
        <!--在与第2个控制器关联的视图上,无法访问与第1个视图相关联的控制器的数据-->
        <div ng-controller="demoCtrl2"></div>
        <div ng-controller="demoCtrl3"></div>
    <script>
        var app = angular.module('hmApp',[]);
        app.controller('demoCtrl1',['$scope',function ($scope) {
            $scope.name = "杰克";
            //为第1个控制器/视图的$scope绑定了一个数据.
            //这个数据只能在与当前控制器相互关联的视图上访问.
            //不能在与别的控制器关联的视图上访问.
        }]);
        app.controller('demoCtrl2',['$scope',function ($scope) {

        }]);
        app.controller('demoCtrl3',['$scope',function ($scope) {

        }]);
    </script>
    </body>
    </html>

  ```

- 2.父子关系的视图所对应的控制器,在子视图/控制器中可以访问父视图/控制器中$scope的数据.

  - 子视图中可以访问父视图中的数据.

  - 父视图不能访问子视图中的数据.

  - 如果访问的变量在视图中有定义,那么优先访问子视图自己的,如果该变量子视图自己没有定义,这个时候再去尝试查找父视图中是否有定义这个数据.

    ```
    <!DOCTYPE html>
    <html lang="en" ng-app="hmApp">
    <head>
      <meta charset="UTF-8">
      <title>Title</title>
      <script src="lib/angular.min.js"></script>
    </head>
    <body>
    <div ng-controller="fatherCtrl">
      <div ng-controller="sonCtrl">
          <span>在子视图中访问父视图作用域中的数据: </span>
          <!--当视图存在父子关系的时候,子视图可以访问父视图的数据-->
      </div>
    </div>
    <script>
      var app = angular.module('hmApp',[]);
      app.controller('fatherCtrl',['$scope',function ($scope) {
          $scope.name = "杰克";
      }]);
      app.controller('sonCtrl',['$scope',function ($scope) {

      }]);
    </script>
    </body>
    </html>

    ```

- 3.根作用域

  - 我们可以使用`ng-init`指令来初始化一个变量,在父级元素上.

  - 那么这个父级元素下所有的子视图都可以访问.

    ```
    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <title>Title</title>
      <script src="lib/angular.min.js"></script>
    </head>
    <body>
      <div ng-app="hmApp" ng-init="name='jack'">
          <div ng-controller="demoCtrl1"></div>
          <div ng-controller="demoCtrl2"></div>
          <div ng-controller="demoCtrl3"></div>
      </div>
      <script>
          var app = angular.module('hmApp',[]);
          app.controller('demoCtrl1',['$scope',function ($scope) {

          }]);
          app.controller('demoCtrl2',['$scope',function ($scope) {

          }]);
          app.controller('demoCtrl3',['$scope',function ($scope) {

          }]);
      </script>
    </body>
    </html>
    ```

## 过滤器

```
在AngularJS中使用过滤器格式化展示数据，在“{{}}”中使用“|”来调用过滤器，使用“:”传递参数。
```

### 内置过滤器

- 日期过滤器 `｛{now|date:'yyyy-MM-dd hh:mm:ss'}}`

- 货币符号过滤器 `｛{price|currency}}`默认是美元符号如果想要显示其它货币符号`｛{price|currency:'￥'}}这样显示的就是人民币符号`保留指定位数的小数`｛{price|currency:'￥':2}}这样显示的就是人民币符号 并四舍五入保留两位小数`

- 转换为大写

  ```
    ｛{info|uppercase}}
     将info的值转换为大写显示

  ```

- 转换为小写

  ```
    ｛{info|lowercase}}
     将info的值转换为小写显示

  ```

- 截取数组/字符串中指定位数的元素.

  ```
    ｛{arr|limitTo:n}}
     正数从左往右截取n个元素
     负数从右往左截取n个元素
     arr可以是1个数组
     也可以是一个字符串.字符串的话就截取每一个字符.

  ```

- 处理数字的过滤器`number`可以控制小数的位数`  ｛{num|number:2}} 保留2位小数输出.`

- json过滤器 将对象转换为json字符串

  ```
    ｛{obj|json}} 将obj对象转换为json字符串输出.实际上,不使用json过滤器它也会这么做.

  ```

- orderBy过滤器

  ```
    ｛{students|orderBy:'score'}} 将student数组中的对象以score属性为参照进行排序 默认是升序.
    ｛{students|orderBy:'score':true}} 降序

  ```

- filter 过滤器

  ```
    ｛{students|filter:{score:90} }} 过滤出数组中对象分数等于90的对象.
     特别注意: 参数对象必须和后面的大括弧有一个空格.
  ```

### 自定义过滤器

- 模块对象提供了一个filter方法,允许我们自定义过滤器.

- 该方法的参数说明

  - 第一个参数: 过滤器名称

  - 第二个参数: 回调函数 - 当执行我们自定义的过滤器的时候,就会自动来执行这个回调函数.

    ```
      <div ng-controller="demoCtrl">
          ｛{name|highven}}
      </div>

      <script>
          var app = angular.module('hmApp', []);
          app.controller('demoCtrl', ['$scope', function ($scope) {
              $scope.name = "jack";
          }])
          app.filter('highven',function () {
              console.log("我被执行了");
          });
      </script>

    ```

- 通过调试发现,回调函数确实被执行了,但是报错了.报错的原因是我们没有按照要求来写这个回调函数的参数和返回值.

- 要求这个回调函数必须返回一个函数.返回的这个函数就是过滤器,来处理过滤数据的.

- 这个返回的函数

  - 第1个参数: 需要处理过滤的数据.

  - 后面的参数: 处理数据的时候,自己还需要的另外的参数

  - 返回值: 处理完毕后返回的数据,被显示出来.

    ```
    <!-- 就会将name传递给自定义过滤器返回的函数处理 最终显示函数的返回值 -->
    <span>｛{name|highven}}</span>
    <script>
      app.filter('highven',function () {
          return function(data){
              return data+"哈哈";
          }
      });
    </script>

    ```

- 自定义过滤器案例:将一个英文句子中首个单词的首字母大写.

  ```
    app.filter('firstBig',function () {
        return function (data) {
            return data[0].toUpperCase()+data.slice(1);
            //slice从指定位置提取字符串 没有第2个参数就一直提到最后.
        }
    });
  ```

## 依赖注入

```
Angular内部封装了很多的模块,我们作为开发者在进行开发的时候,直接拿来使用就行，
也就是说,如果我们要使用别人封装好的模块,就必须要先引入别人的模块.
没有这个模块,可能就实现不了这个功能.
也就是我们依赖于这个模块.
比如jQuery是我们依赖的.

```

- 理解依赖注入
  - 依赖关系: 就是模块之间的依赖关系.比如`bootstrap`依赖于`jQuery`,它们之间的关系就是依赖关系.
  - 依赖解决: 建立这种依赖关系的方案.比如之前我们使用1个`scripr.src`来解决依赖关系.
  - 注入: 是解决依赖的另外一种方式. 你可以形象的理解，A依赖于B,那么就像打针一样,把B注入到A中,那么A中就可以使用B了.它们的依赖关系就建立成功了.
  - 所以,依赖注入是建立依赖关系的一种方式.

### 行内式注入

- 在视图中之所以能够访问到控制器绑定到$scope中的值,完全是因为$scope的存在.
- 实际上,$scope是Angular的一个模块.这个模块在视图中可以直接访问使用.
- 但是在控制器的回调函数中,无法直接访问使用这个$scope模块.
- 所以,这个回调函数必须要依赖$scope模块.
- 创建控制器的时候.第2个参数是一个数组.
- 数组的最后一个元素是控制器的回调函数.
- 前面的元素其实就是表明回调函数要依赖Angular的那些模块.
- `app.controller('demoCtrl', ['$scope', function ($scope) {}])`第1个元素. '$scope' 表明控制器要依赖$scope这个模块.回调函数的参数: Angular会将$scope模块通过函数的形参注入到函数的内部,让函数去使用.实际上,回调函数的形参是可以任意的,这里之所以取得和模块的名字一样,是为了让我们的代码看起来更加具备可读性.Angular提供的模块还有很多,我们也可以将其注入到控制器中.`app.controller('demoCtrl', ['$scope','$http' function ($scope,$http) {}])表明,控制器要依赖$scope模块和$http模块.那么这个时候,Angular会将这两个模块通过函数的形参`按照顺序`注入.`
- 这样的注入方式,我们就叫做`行内式注入``                                                  var app = angular.module('hmApp', []);          /*          * 第二个参数是一个数组.          *      数组的第一个元素, '$scope'表示控制器要依赖 $scope 这个模块.          *      Angular会通过回调函数的参数将$scope模块注入到回调函数内部.          *      供控制器回调函数内部使用.          *      这个时候,回调函数内部就可以通过形参拿到$scope这个模块.          *      将其与视图共享之,传递数据之.          */          app.controller('demoCtrl', ['$scope', function ($scope) {                  $scope.name = "杰克";          }])        `

### 推断式注入

- 推断式注入的写法很简单,第2个参数直接写1个回调函数就可以.

  ```
   app.controller('demoCtrl', function ($scope) {
        $scope.name = "杰克";
   });

  ```

- Angular在注入的时候,会根据回调函数的参数名称进行推断.

- 如果参数名称是$scope,那么就会将$scope这个模块进行注入

- 如果参数名称是$http,那么就会将$http这个模块进行注入

- 所以,使用这种注入方式,回调函数的形参必须要和Angular的模块名称一致.否则将无法注入.

- 推断式注入的缺点： 当进行代码压缩的时候,就会出问题,因为代码压缩会将形参替换.那么这个时候Angular就无法正常注入了.

- 所以,我们推荐使`行内式注入`.

## Angular服务

```
服务，可以理解为就是一个对象或者函数,对外提供特定的功能.
其实你完全可以认为它就是一个模块,不同的模块提供不同的功能.
当我们要使用某1个模块的时候,将其注入到控制器中便可以使用.
```

### $log服务

- 作用:在控制台输出调试信息. $log是1个对象.
- 调试信息分为如下几个级别.
  - `error` 错误信息
  - `debug` debug信息
  - `info` 打印信息
  - `log` 正常打印日志
  - `warn` 警告信息
- 分别调用$log对象的这几个方法就可以输出对应格式的信息.
- 注意： 要正确调整浏览器控制台log过滤.

### $timeout服务



作用：在指定的时间做事情,$timeout是一个函数.`  


  我的名字叫做｛{name}}


​      var app = angular.module('hmApp', []);
​      app.controller('demoCtrl', ['$scope','$timeout', function ($scope,$timeout) {
​          $scope.now = new Date();
​          //表示3秒钟后为name赋值
​          $timeout(function () {
​              $scope.name = "小明";
​          },3000);
​      }]);

  ### $interval服务

- 作用:每隔指定的时间就做指定的事情.

  ```
    <body>
    <div ng-controller="demoCtrl">
        <!--所以,这里的数据每一秒钟就变化一次-->
        <p>现在时间是:｛{now|date:'yyyy-MM-dd HH:mm:ss'}}</p>
    </div>
    <script>
        var app = angular.module('hmApp', []);
        app.controller('demoCtrl', ['$scope','$interval', function ($scope,$interval) {
            $interval(function () {
                $scope.now = new Date();
            },1000);//每隔一秒钟就为now重新赋值.
        }]);
    </script>
    </body>

  ```

- $interval函数,返回1个数据.调用`$interval.cancel(返回值)`可以停止计时器`          现在时间是:｛{now|date:'yyyy-MM-dd HH:mm:ss'}}      停止          var app = angular.module('hmApp', []);      app.controller('demoCtrl', ['$scope','$interval', function ($scope,$interval) {          var stop = $interval(function () {              $scope.now = new Date();          },1000);          $scope.stop = function () {              $interval.cancel(stop);          }      }]);    `

### $http服务

#### $http服务的基本使用

- 作用:用于向服务器发送异步请求 这是1个函数.

- 参数:传入1个符合条件的对象.

  - `url`:请求地址
  - `method`:请求方式get/post
  - `data`:{} 当请求方式为post的时候 使用data传递数据.
  - `params`:{} 当请求方式为get的时候,使用params传递数据.
  - `headers`:{} 设置请求头信息

- `.then()`函数传入两个回调函数.第1个回调,当请求成功后执行,参数`info`。通过info.data拿到返回的数据第2个回调,当请求失败后执行.

- 案例演示

  ```
    <body>
        <div ng-controller="demoCtrl">
            <table>
                <tr>
                    <th>姓名</th>
                    <th>年龄</th>
                </tr>
                <tr ng-repeat="stu in data"><td>｛{stu.name}}</td><td>｛{stu.age}}</td></tr>
            </table>
        </div>
        <script>
            var app = angular.module('hmApp', []);
            app.controller('demoCtrl', ['$scope','$http',function ($scope,$http) {
                $http({
                    url:'example.php',
                    method:'get'
                }).then(function (info) {
                $scope.data = info.data;
                },function () {

                });
            }]);
        </script>
    </body>
  ```

#### $http服务传递数据的 格式

- 当请求类型是`get`时,向服务器传递的数据必须要放在`params`中，以对象的形式.

  ```
    <div ng-controller="loginCtrl">
        用户名: <input type="text" ng-model="uName">
        <br>
        密码: <input type="password" ng-model="pwd">
        <br>
        <button ng-click="login()">登录</button>
    </div>
    <script>
        app.controller('loginCtrl', ['$scope', '$http',function ($scope,$http) {
            $scope.login = function () {
                $http({
                    url:'login.php',
                    method:'get',
                    params:{
                        uName:$scope.uName,
                        pwd:$scope.pwd
                    }
                }).then(function (info) {

                }).catch(function () {

                });
            }
        }]);
    </script>

  ```

- 当请求类型是post时,向服务器发送的数据必须要放在`data`中.设置发送数据的类型.`data`要以键值对的字符串形式.

- 客户端以post方式向服务器发送数据时.必须要指定发送数据的类型.

- 因为不同的数据格式在服务器处理的方式是不一样的.

- 常见的数据格式

  - application/json --> 这种格式叫做formdata
  - application/x-www-form-urlencoded --> 这种格式叫做payload

- jQuery的Ajax默认的数据类型就是`application/x-www-form-urlencoded`

- AngularJS的$http默认支持的是`application/json`

#### .$http跨域

- 基于浏览器的同源策略,Ajax异步是无法实现跨域请求的.
- 实现跨域请求的解决方案
  - src属性是天然支持跨域的.
  - 所以,我们可以利用`script`标签的`src`属性来跨域请求数据.
  - 如果使用`script`标签的`src`属性来跨域请求,会将请求回来的数据作为js代码执行

##### AngularJS的跨域

AngularJS已经帮我们封装好了一切.

```
  $http({
      url:'',//请求地址
      method:'jsonp',
      params:{
          //传递额外数据.
      }
  }).then(function(info){

  }).catch(function(){

  });
```