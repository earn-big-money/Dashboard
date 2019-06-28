
##  2. <a name=''></a>技术选型
###  2.1. <a name='client'></a>client端
可选的技术选型及其选择理由分析
- 前端框架

  - Vue

    Vue是一套用于构建用户界面的渐进式框架，可以自底向上逐层应用。Vue容易上手，便于与第三方库整合（例如element-ui），另外Vue是中国开发的前端框架，官方文档全中文，便于学习使用，另外开发人员之前有学习过Vue，所以采用Vue来搭建前端是最合理的选择。

  - element-ui

    element-ui是一个与Vue兼容的桌面端组件库，该组件库中包含众多网站开发中常用的控件，如下拉菜单，导航栏，进度条等等，官网上每个例子后面都有实现代码，方便易用，而且这些控件UI十分优美，可以极大地提高用户体验。

  - jQuery

    jQuery的重要性不言而喻，控制页面组建的最方便的js包。在前端开发的过程中，将jQuery嵌入到了Vue中，加速了前端页面的开发。

###  2.2. <a name='server'></a>server端
可选的技术选型及其选择理由分析

- 后端框架
  - nodejs
    选用nodejs达到前后端一致，减少可能会出现的语言支持不一致导致的坑。并且因为这次的项目并不是一个计算密集的项目，所以没必要考虑分布式服务，nodejs在性能上足够达成需求。
  - go
    高性能，对于中间件支持较好，但是因为这是一个团队项目，贸然使用一个大家熟练程度不同的技术栈最严重的后果就是因为熟练程度不同导致部分同学编程bug生成机器，写的bug比写的task还更多，平白无故耗费其他同学的精力，对于项目的效率来说是一个负提升。
  - django
    后端数据库二合一，小白学习后端第一个应该学的后端框架，虽然说简单但是还是因为和go一样的原因导致不被采用。

所以我们后端框架选择的是nodejs作为大家开发的统一框架。

- 后台服务支持
  没什么好说的，Nginx，傻瓜式操作。

- 数据库DBMS
  - sql
    最常用的数据库DBMS类型，优化好效率高，只能对大数据量低并发的不二之选，因为上过数据库的课所以大家都会用。
  - nosql
    现在web架构必不可少的分布式数据库DBMS，一句话问就是分布式，针对对于上锁频率不高的服务来说非常完美，相对于sql的时候可操作性更大。
    
  但是还是因为效率负提升的考虑，最后还是选用了mysql作为数据库的技术栈。
- 额外的技术支持
  - docker
    容器化服务，即插即用的特性

##  3. <a name='-1'></a>软件架构设计

###  3.1. <a name='-1'></a>1. 软件架构的逻辑视图

![](./documents/assets/logic_arch.PNG)

架构是前后端分离，前端发放服务器和后端交互服务器分离，其中用restful-like api进行交互。用mysql作为持久化层。

前端的模式为mvc模式，其中使用到的外部支持库有编辑调查表的survey.js

###  3.2. <a name='-1'></a>2. 软件架构的物理视图

![](./documents/assets/physics_arch.PNG)

架构的物理层架构，分别分成了前端用户的浏览器访问端，从静态服务器中获取前端文件，用restful的方式从api服务器去进行交互，其中涉及到持久层的交互由与mysql dbrs完成。





#### 前端文件目录

- front-end
  - build:  webpack文件，配置参数,打包的代码存放在这里，自动生成
  - config:  vue项目的基本配置文件，自动生成
  - node_modules: 存放项目中使用的各种npm包，cnpm/npm install后生成
  - src: 项目源文件存放地址，包含前端页面，路径配置，静态资源等
    - assets：存放前端页面用到的各种静态资源
    - components：存放前端的各个vue页面
    - router：存放前端页面的路径配置文件
    - App.vue：VUE demo演示页面的启动组件
    - main.js：该模块页面的初始化js
  - static：项目静态资源目录
  - test：测试文件，初始化测试都写在这里,可以删除
  - .babelrc ：babel编译参数，vue开发需要babel编译
  - .editorconfig：代码编辑环境配置文件
  - .gitignore：设置git忽略文件
  - .postcssrc.js：css配置文件,自动补齐浏览器css前缀
  - index.html：主页，项目入口文件
  - package.json：项目配置文件，描述项目信息和依赖
  - README.md ：项目的说明文档，markdown 格式
  - run.bat：Windows批处理文件，运行项目时生成

  # 后端源码目录以及说明
## 项目代码  
https://github.com/whatsup-sysu/Backend

## 代码说明
- src
  - bin: 执行程序
  - controllor:  控制器目录
    - DBController_public.js:数据库接口
    - userSystem_public.js:用户系统，登录注册等
    - dutySystem_public.js:任务系统，发布接受等
    - tradeSystem_public.js:交易系统，转账充值等
    - surveySystem_public.js:问卷调查相关
    - imageSystem_public.js:图片资源上传下载
    - utils_public:公共模块
    - validator.js:正则校验
  - database: 数据库管理
    - Config：数据表及配置信息
    - DataBaseMySQL：数据库连接管理
  - routes：路由分级处理
    - users.js 
    - dities.js
    - photo.js
    - survey.js
    - trades.js
    - survey.js
  - sessions：保存后端与前端的会话状态
  - upload：保存用户上传的资源信息
  - app.js ：express程序执行入口
  - package.json：项目配置文件，描述项目信息和依赖

## 测试文档  
附文件《后端API测试报告》


##  4. <a name='-1'></a>模块划分


###  4.1. <a name='client-1'></a>client端

- 前端的划分主要体现在页面的划分上。前端根目录的src文件夹是需要自己编写的部分，里面记录了页面文件以及路由配置。为了便于管理，路由配置全部放到了index.js文件中。前端页面全部放到components文件下。前端的分工主要体现在页面的分工上，不用的人完成不用部分的页面。前端页面总共分为8个模块，分别为

  - 创建任务（CreateTask）
  - 个人信息（Information）
  - 登录（Login）
  - 注册（Register）
  - 首页（MainPage）
  - 问卷系统（Survey）
  - 任务详细信息（包含接受任务流程）(TaskDetail)
  - 图片管理（Photo）

  这个7个模块用到的vue页面，js，css以及静态资源等全部独立地放到不同的文件夹中。



###  4.2. <a name='server-1'></a>server端

- 后端的划分主要体现在了功能或者说是逻辑的划分上。后端将各个具体的功能模块进行充分的抽象和分层：routes用来控制路由的跳转，database抽象数据库的各项操作，controller则是二者之间的衔接模块，根据上层路由的请求调用底层的数据库方法。app.js位于最顶层，通过调用routes来统领全局。
- routes和controller中主要包含如下一一对应的模块：
  - 个人信息(users)
  - 主页(index)
  - 事务(duties)
  - 问卷(survey)
  - 交易(trades)
  - 图片(photo)


##  5. <a name='-1'></a>详细解释具体设计在源码中的体现
###  5.1. <a name='client-1'></a>client端

- 结构化编程：为了便于前端的分工，将前端需要实现的页面以及业务流程进行了划分，大致分为了8个模块，分别为创建任务（CreateTask），个人信息（Information），登录（Login），注册（Register），首页（MainPage），问卷系统（Survey），任务详细信息（包含接受任务流程），(TaskDetail)，图片管理（Photo）。划分好模块之后编程变得更加容易。

  前端模块源码链接：https://github.com/whatsup-sysu/Frontend/tree/master/whatsup/src/components

- 回调函数，使用回调函数异步地向后端发送请求，支持了并发访问，优化用户体验。

```
//例子：首页在创建的时候需要向后端清楚数据，将目前正在发布中的任务数据保存到前端寄存器，便于任务的显示
//以及对任务的各种操作。请求数据采用异步请求使用回调函数来进行实现。
created: function() {
    this.uid = this.$route.query.uid
    if(this.uid==null){
      this.uid=$("#username").text();
    }
    if(this.id==null){
      this.uid = this.$cookies.get('id')
    }
    //如果当前没有任务数据的话就异步地向后端请求数据
    if(this.nowduty==null){
      var _self = this;
      //采用ajax的方式异步请求
      $.ajax({
        type: 'GET',
        url: '/api/duties/screen?pageNumber=1&countPerPage=7&sortType=time&sortOrder=ascend',
        dataType: 'json',
        timeout: 3000,
        success: function(result, xhr) {
        
          //成功请求数据之后的回调函数，解析并保存得到的数据
          console.log(result)
          _self.nowduty = result['content']
          _self.nowpage = 1
          _self.nowdutynum = result['count']
          if(_self.nowdutynum<7){
            for(var i=_self.nowdutynum;i<7;i++){
              _self.nowduty.push(0);
            }
          }
          //根据得到的数据动态修改页面内容
          for(var i=0;i<7;i++){
            if(_self.nowduty[i]!=0){
              var content="#dcontent"+(i+1).toString();
              $(content).text(_self.nowduty[i].dintroduction);
              var type = "#dtype"+(i+1).toString();
              $(type).text(_self.nowduty[i].dtype);
              var title = "#dtitle"+(i+1).toString();
              $(title).text(_self.nowduty[i].dtitle);
              var sponsor = "#dsponsor"+(i+1).toString();
              $(sponsor).text(_self.nowduty[i].dsponsor);
              var modifyTime = "#dmodifyTime"+(i+1).toString();
              $(modifyTime).text(_self.nowduty[i].dmodifyTime);
              var curaccepters = "#dcuraccepters"+(i+1).toString();
              $(curaccepters).text(_self.nowduty[i].curaccepters);
            } else {
              //alert("hidden");
              var id="#u128-"+(i+1).toString();
              $(id).css("visibility","hidden");
            }
          }
        },
        //请求数据失败之后的回调函数，提示出错，输出错误信息。
        error: function(result, xhr) {
          console.log(result)
          alert('服务器连接错误: ' + xhr)
        }
      })
    }
  }
```



###  5.2. <a name='server-1'></a>server端
后端架构设计技术：
* Service Oriented Architecture  
首先后端是按照面向服务的体系结构开发的，它按照一个基于RESTFUL风格标准定义的API接口文档。服务是最核心的抽象手段，业务被划分为一系列粗粒度的业务服务和业务流程。  
架构开发思想主要体现在[API文档](https://github.com/whatsup-sysu/documents/blob/master/%E6%BA%90%E4%BB%A3%E7%A0%81%E7%9B%AE%E5%BD%95%E5%8F%8A%E8%AF%B4%E6%98%8E/%E5%90%8E%E7%AB%AFAPI%E6%96%87%E6%A1%A3.html)，之后的接口发开都是基于接口文档的标准进行。

* Object-Oriented Programming  
后端在路由分级后按照业务类型抽象了几个处理不同类型业务的对象类型，如userSystem、dutySystem、tradeSystem等等。这些对象封装了相关的业务逻辑方法。抽象的对象列表相关代码主要在[控制器目录](https://github.com/whatsup-sysu/Backend/tree/master/src/controller)中。