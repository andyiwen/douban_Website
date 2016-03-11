NodeJs+MongoDB+jQuery仿豆瓣电影音乐网站搭建
================================================

简介:
---------------
本项目电影和音乐首页交互代码是由jQuery完成的，在<a href="https://github.com/Loogeek/douban-react" target="\_blank">douban-react</a>项目中尝试了将部分代码使用React来重写，提高了阅读性和维护性，可以参考下。


* 项目后端搭建:
  * 使用NodeJs + express完成电影网站后端搭建;
  * 数据库选择mongodb,使用mongoose来完成对mongodb快速建模;
  * 使用jade后端模板引擎完成页面创建渲染;
  * 以上模块都也可以通过npm包管理工具来进行安装

* 项目前端搭建:
  * 使用npm模块处理前端静态资源的版本依赖和管理;
  * 通过jQuery和Bootsrap完成网站前端JS脚本和样式处理;
  * 使用Sass完成电影和音乐首页样式;
  * 使用validate插件完成账号注册登录判断
  * 使用Ajax与后端进行交互;

* 本地开发环境搭建:
  * 使用Grunt集成Sass文件编译、压缩、样式合并、使用jshint完成语法统一检查、使用mocha完成单元测试、服务的自动重启等功能

* 网站整体功能:
  * 豆瓣电影和音乐相同展示页面
  * 用户注册登录;
  * 电影评论;
  * 电影搜索查找;
  * 电影音乐分类管理及搜索;
  * 列表分页处理;
  * 电影音乐海报图片上传;
  * 可同步豆瓣电影音乐数据方便新数据添加;
  * 访客统计;
  * 简单的用户账号单元测试;

项目整体效果
-------
<div>
  <img src="https://raw.githubusercontent.com/Loogeek/douban_Website/master/ReadmeImag/doubanMovie.png" width="50%" float"left" height="700" alt="电影首页"/>
  <img src="https://raw.githubusercontent.com/Loogeek/douban_Website/master/ReadmeImag/doubanMusic.png" width="45%" float"left" height="700" alt="音乐首页"/>
</div>
<div text-align="center">
  <img src="https://raw.githubusercontent.com/Loogeek/douban_Website/master/ReadmeImag/doubanDetail.png" width="50%" alt="电影详情"/>
</div>

动态效果演示
-------
[动态效果演示](http://7xrqxi.com1.z0.glb.clouddn.com/douban.gif)

Node版本:
-------
目前在4.2.x版本下运行正常

安装:
----
- 安装mongodb(https://www.mongodb.org/downloads#production)完成相关配置;
- 在当前项目目录中使用npm install命令安装相关模块;

运行与使用:
----
1. 启动数据库`mongod`,如果出现错误尝试输入`sudo mongod`来完成启动
2. 项目目录下的doubanDatabase是可供选择导入的数据库信息，可通过命令`mongorestore -h host -d dataName --dir=path` 来导入该文件夹信息到数据库中，其中-h是连接地址，如127.0.0.1 -d是将要创建数据库的名称，如douban(注意:项目中链接的数据库名称是douban,如果-d后创建的数据库名称叫douban2,则需要将app.js文件`dbUrl = 'mongodb://127.0.0.1/douban`中的douban改成douban2),--dir=后为该doubanDatabase所在路径，具体可通过`mongorestore --help`查看
3. 使用命令行工具在该项目目录下使用grunt运行程序,默认是使用3000端口，若端口已占用可在gruntfile.js文件中nodemon配置下将PORT设置成一个未占用端口，当命令行工具看到：Movie started on； port:3000时在游览器中输入localhost:3000即可看到项目电影主页;
4. doubanDatabase中存储了默认的管理员账号:1234 密码:1234 权限为50，只有当权限大于10才可以访问后台控制页面，可通过修改数据库中users中role值完成用户权限控制。


项目页面:
-------
当使用管理员账号登录时(数据库中默认是1234)可在顶部搜索栏下显示各后台控制页面的链接，方便页面切换。

* 豆瓣电影首页: localhost:3000/  豆瓣音乐: localhost:3000/musicIndex

* 用户后台页:
- 用户注册页面: localhost:3000/signup
- 用户登陆页面: localhost:3000/signin
- 用户详情列表页: localhost:3000/admin/user/list

* 电影后台页:
- 详情页:localhost:3000/movie/:id
- 后台录入页:localhost:3000/admin/movie/new
- 列表页:localhost:3000/admin/movie/list
- 分类录入页:localhost:3000/admin/movie/movieCategory/new
- 分类页:localhost:3000/admin/movie/movieCategory/list
- 电影院录入页:localhost:3000/admin/movie/programme/new
- 电影院列表页:localhost:3000/admin/movie/city/list

* 音乐后台页:
- 详情页:localhost:3000/music/:id
- 后台录入页:localhost:3000/admin/music/new
- 列表页:localhost:3000/admin/music/list
- 分类录入页:localhost:3000/admin/music/musicCategory/new
- 分类页:localhost:3000/admin/music/musicCategory/new
- 热门榜单列表页:localhost:3000/admin/music/programme/list

后期完善:
-------
* 1.部分功能还有待完善;
* 2.尝试使用React/Vue等框架完善网站功能，减少多DOM的直接操作，方便后期维护
