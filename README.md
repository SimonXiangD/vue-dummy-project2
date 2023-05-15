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

