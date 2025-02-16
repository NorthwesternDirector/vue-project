## APP 小demo！一起追寻改bug的快乐！！
> 该demo主要是实践与熟悉一下vue的各个功能模块，包括了  `vue-resource` `vue-router` `vuex` `webpack` `vue组件化` `vue生命周期` `vue动画`
#### demo样式展示：<br>
<div align=center><img height=334px width=186px src="https://github.com/NorthwesternDirector/vue-project/blob/master/src/images/captures/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202019-08-31%20%E4%B8%8B%E5%8D%8810.22.15.png">&nbsp;&nbsp;&nbsp;<img height=334px width=186px src="https://github.com/NorthwesternDirector/vue-project/blob/master/src/images/captures/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202019-08-31%20%E4%B8%8B%E5%8D%8810.23.28.png">&nbsp;&nbsp;&nbsp;<img height=334px width=186px src="https://github.com/NorthwesternDirector/vue-project/blob/master/src/images/captures/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202019-08-31%20%E4%B8%8B%E5%8D%8810.23.37.png">&nbsp;&nbsp;&nbsp;<img height=334px width=186px src="https://github.com/NorthwesternDirector/vue-project/blob/master/src/images/captures/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202019-08-31%20%E4%B8%8B%E5%8D%8810.24.28.png"></div><div align=center><img height=334px width=186px src="https://github.com/NorthwesternDirector/vue-project/blob/master/src/images/captures/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202019-08-31%20%E4%B8%8B%E5%8D%8810.35.53.png">&nbsp;&nbsp;&nbsp;<img height=334px width=186px src="https://github.com/NorthwesternDirector/vue-project/blob/master/src/images/captures/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202019-08-31%20%E4%B8%8B%E5%8D%8810.25.09.png">&nbsp;&nbsp;&nbsp;<img height=334px width=186px src="https://github.com/NorthwesternDirector/vue-project/blob/master/src/images/captures/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202019-08-31%20%E4%B8%8B%E5%8D%8810.25.18.png">&nbsp;&nbsp;&nbsp;<img height=334px width=186px src="https://github.com/NorthwesternDirector/vue-project/blob/master/src/images/captures/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202019-08-31%20%E4%B8%8B%E5%8D%8810.25.36.png"></div>

---

#### part1 制作首页app组件
`vue-router` `vue-resource` `Mint-UI` `MUI`

1. 完成header区域
* 使用Mint-UI中的header组件

2. 制作底部的tabbar区域(使用 MUI的Tabbar.html)
* 2.1
    * 改造tabbar为router-link
    * 设置路由高亮类
    * 点击tabbar中的路由链接，展示对应的路由组件

3. 在中间区域使用 router-view 展示路由匹配到的组件
* 3.1
    * 首页轮播图
    * 本来想使用vue-resource请求远程数据
    * 利用this.$http.get 
    * 最后用了 本地的
* 3.2
    * 首页九宫格
    * 利用本地图片及scss改造样式

#### part2 近期旅行、评论子组件
`vue-router` `vue-resource` `MUI`

1. 九宫格-近期旅行
* 1.1
    * 改造 近期旅行 路由链接
    * 绘制界面 ：使用MUI中的media-list.html
    * 使用vue-resource 获取数据
    * 渲染数据
    * 1.2
    * 实现 近期旅行列表 点击跳转到旅行详情
    * 把列表中的每一项改造为 router-link，同时，在跳转时候提供唯一标识符
    * 创建旅游详情的组件页面 newsInfo.vue
    * 在路由模块中，将旅游详情的 路由地址 和 组件页面对应起来
    * 1.3 
    * 实现 旅游详情 的 页面布局 和数据渲染

2. 评论子组件
* 2.1
    * 单独封装一个 comment.vue评论子组件
    * 在需要 评论组件 的页面import一下
    * 在父组件中，使用‘component’属性，将导入的组件注册为自己的子组件
    * 在注册子组件时注册名称，在页面中以标签形式引入
    * 使用属性绑定的方式实现 父子组件传值
    * 2.2
    * 为 加载更多 绑定点击事件，请求下一页数据
    * 点击后 pageIndex++，再次调用getComments()
    * 2.3
    * 发表评论功能，为文本框做数据双向绑定，为发表按钮添加事件
    * 评论成功后，在客户端手动拼接出一个最新的评论对象，追加到data中的comments开头

#### part3 图片分享、商品子组件
`vue-router` `vue-resource` `MUI`

1. 图片分享子组件
* 将图片分享按钮改造为路由链接，并显示对应的组件页面
* 1.1
    * 绘制图片分享组件的样式
    * 制作顶部滑动条，借助MUI中的 tab-top-webview-main.html
    * 滑动条是JS组件，需要导入mui.js,并使用官方方式初始化
    * mui.js与bundle.js默认启动的 严格模式冲突：把webpack的严格模式禁用
    * 初始化滑动条需要等DOM元素加载完毕，所以需要将 初始滑动条 挂载在mounted()钩子函数
    * tabbar和mui.js文件类名可能冲突导致无法滑动,自己换个类名
    * 获取所有分类，渲染分类列表
* 1.2
    * 获取图片列表
    * 图片列表使用懒加载技术，使用 Mint-UI 提供的组件 lazy-load
    * 美化样式
* 1.3
    * 使用router-link(使用tag属性将其渲染为一个li)绑定跳转到图片详情页面
    * 图片详情
    * 实现图片详情的缩略图功能，使用插件vue-preview

2. 商品子组件
    * 绘制页面结构并获取数据

3. 尝试在手机调试项目

#### part4 商品详情子组件

1. 商品详情子组件
    * 在跳转物品详细页面时，使用编程式导航（使用window.location.herf 的形式跳转）
    * 将轮播图抽离为一个子组件
    * 数据绑定，页面美化
    * 商品+1小球飞购物车，涉及到“父子组件传值”以及“子父组件传值”

#### part5 vuex
`Vuex` 

1. Vuex学习
    * Vuex 是为了保存组件之间共享数据而诞生的（可代替父子组件传值）
    * 共享数据放置在Vuex内，非共享数据放在组件内的data上即可
    * 🌟prop存放父组件的传值，data存放组件私有数据，Vuex存放组件间共享数据
    * 通过this.$store.state.参数名 访问参数
    * 通过this.$store.commit('方法名','唯一参数') 调用对参数进行操作的方法
    * 通过 this.$store.getters.参数名，调用getters:{}属性内的包装后的数据（类似filter）
* 1.1 
    * 将添加物品的信息全部存储在store内，方便购物车徽标、购物车结算等功能之后的使用
    * 利用 localStorage 将购物车信息本地持久化存储
    * Vuex的持续学习。。。



