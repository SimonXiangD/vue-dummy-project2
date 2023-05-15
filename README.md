# vue入门项目2
类似之前写的mysteryLand，就是很基础的资料管理，可以展示创建删除。但是没有数据库，网页刷新就没了。

使用方法：

npm i 


npm run serve

然后打开localhost 8081端口

感觉用vue写确实方便很多，思路大概为：
开局创建项目；
创建App.vue ，然后创建Theheader和TheResources界面。前者就是个ui界面，主要的工作是在后者。

在正式开始写之前，可以先创建一些ui模板（虽然实际上并不是一开始就这么写的）：
创建button和card对应的ui，用到了slot。然后这种基础ui的componet是要在app.js里声明的，而其他component可能local声明更好些；button拥有的props对应type和class，于是可以在之后借此方便的改变button外观。
使用slot时，可以用默认的，也可以加名字。

回到正题，
然后TheResources.vue负责数据的记录与主界面，然后使用dynamic component控制哪个界面：是展示所有card，还是创建新card？。用一个selectedStatus记录状态。
如果有需要，得用keep-alive，防止切换component时其他component重置。

然后就是写展示所有card了。要展示所有的，那先得可以展示一个。就写展示一个的，props需要card信息， 然后还要有一个delete按钮。delete就用inject来实现祖孙信息传递，参数用id就好

展示所有的，就是引入展示一个的component。父结点用provide，它用inject获得所有card的信息，然后v-for展示就行。

添加card，就是写一个form，input里都用ref。然后inject进一个添加元素的函数。然后设计到判定输入无效时，我看的课程讲的办法是用一个isInvalidInput记录。
如果输入不符合规范，就v-if展示出一个dialog（用ui重写过），然后里面有几个不同的slot，展示不同的信息，还有一个按钮，可以emit信息到父结点。说实话style以后的dialog还挺好看的。但我觉得没必要这么麻烦，直接用bootstrap，给input加上form-contorl类，再加一个required就可以了。不过当规范更加复杂时，或许用dialog要更好一些。


总结一下用到的vue特性：

基础的vue，比如 v-bind (:) v-if v-for v-on ( @ )，都是基础语法；

基础的component操作，主要是template，script两者；

component组件之间的信息交流，方法有proqs父传子，emit子传父，provide/inject祖传孙，refs ... ；

slot的使用，用来传递template，（有点像ejs里的layout）；

动态component，用状态记录然后渲染对应名称的组件；

还有一些其他的，比如vue-style，以及css之类的

























