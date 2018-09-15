##
## 准备工作

+ 进入微信公众号官网 （http://mp.weixin.qq.com）
+ 注册开发者账号（个人、企业），个人的功能少一点，比如直播类/支付类都需要企业级。直播类的就算企业级，上线也需要很多证书与资质。公众号在微信小程序出来之前，分企业号和服务号和订阅号。企业号在前几年流行，小程序出来之后，企业号逐渐式微。现在说公众号大部分都是值得服务号和订阅号，小程序也算一个特殊的公众号，也可以看成独立的服务。
+ 下载微信开发者工具。
+ 登陆小程序后台获取appid。

## 小程序的文件类型

+ 样式CSS-->wxss
+ 骨架html-->wxml
+ 业务js-->js
+ 配置json (json内不可注释！json文件最后如果没有下一条属性，就不要加逗号！和js对象是不同的，以及双引号！)

## 基本组织结构

### 全局文件（必须，不可以更改名字）
+ 全局配置app.json
+ 全局样式app.wxss
+ 全局js！app.js

### pages（必须）
+ 小程序由page组成
+ page里有wxss/wxml/js/json
+ 对于页面文件来说，json不是必须的！

### 环境配置文件
+ project.config.json 无需在意。由微信小程序自动管理。

### utils（属于自定义文件夹）

## 推荐组织结构

### 全局文件（不变）

### pages(需要有组件思想)
+ 除了基本的四个文件，更应该有许多组件。组件中再有基本的四个文件。如果学习过vue/angular/react。或许你可以立马明白。

## flex布局

flex布局并不是微信小程序特有的，但是小程序对她是非常非常支持，而且flex也非常非常好用！

## 组件

### 路径
+ 根目录
+ 相对路径


## 小程序尺寸单位
### 以爱芬6为设计稿时候才是这样的（750*1334  这点要告诉设计师！让她以这个标准设计）
+ px 放到小程序里 /2才是我们想要的！
+ rpx 和设计稿的是1:1 rpx可以自适应！绝大多数都是rpx。

### 以爱粪叉和其他机型设计，也可以换算，但是很麻烦，建议以爱芬6为标准设计。

## 样式
+ 可以在入口文件设置样式。可以给page设置样式，page是小程序给每个页面加的元素，根节点。page的样式可以影响到组件！但是不是所有样式都可以继承。目前开放了color和font。

## 组件
+ 封装性
+ 开放性
+ 可复用
+ 代码分离 维护性！对于绝大多数开发者来说代码分离与维护性是远大于复用性。

## 组件的properties属性
+ type:布尔值，number，string
+ value：（选填）
+ observer:function（选填）

## 实战

###全局配置。
####　json配置。
+ pages:数组类型，配置了路径
+ window：对象类型，全局窗口的表现，用于设置小程序的状态栏、导航条、标题、窗口背景色。
+ tabBar：对象类型，底部或者顶部切换对象，拥有配置字体颜色，以及自身定位，边框颜色，背景颜色，选中颜色。可以通过 tabBar 配置项指定 tab 栏的表现，以及 tab 切换时显示的对应页面。tabBar有一个list选项，接收一个数组，可以配置最少两个最多五个的tab，每一项都是一个对象，用于定义上面的文字，图片，路径。
+ networkTimeout 接受一个对象，配置网络超时。例如发送请求，上传图片，下载图片
+ debug,可以在开发者工具中开启 debug 模式，在开发者工具的控制台面板，调试信息以 info 的形式给出，其信息有Page的注册，页面路由，数据更新，事件触发等。可以帮助开发者快速定位一些常见的问题。
+ functionalPages 启用插件功能页时，插件所有者小程序需要设置其 functionalPages 为 true。
+ requiredBackgroundModes 申明需要后台运行的能力，类型为数组。目前支持以下项目：audio后台播放。

### 配置引入组件。
+ 在page里面的json，定义usingComponents，接收一个对象，写入一个键值对，key是自己定义，value是些上路径。然后在wxml中引入你写的key即可。