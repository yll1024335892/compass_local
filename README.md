# 用compass-style的SASS的框架环境搭建
### 官网
[compass-style.org](http://compass-style.org/)
### 安装rube的环境
针对win下的安装[rubyinstaller.org](https://rubyinstaller.org/)下载Rube+Devkit对应的版本，检查是否安装成功通过指令**ruby -v**
### 通过rube安装compass
**gem install compass**  版本为:**1.0.3**
### 通过rube安装sass
**gem install sass -v 3.4.7**  版本为**3.4.7**
# 工程的创建
### 生成config.rb的文件
- **compass create projectName**操作指令创建compass的工程，我们的目的就是获取这个文件。
- 建立工程文件目录结构**css**,**scss**,**images**,**javascripts**（同时修改下config.rb中对应的文件夹的名字）
- cd+工程的根目录,允许**compass watch**就可以动态的将scss编译为css
- [scss/compass](https://github.com/Compass/compass/tree/stable/core/stylesheets/)的来源，修改了下@import里面修改为相对路径
- 在scss文件夹中建立一个index.scss的文件
```
	@import "compass/css3";
	.xx{
		@include border-radius(0.5px);
	}
```
``` 编译后
	.xx {
		-moz-border-radius: 0.5px;
		-webkit-border-radius: 0.5px;
		border-radius: 0.5px;
	}
```
```
//线性渐变  其中lighten(red, 20%)是使用sass的加亮顏色功能
.box{ @include background(linear-gradient(lighten(red, 20%), red));}
```
### Sprite的处理
```
@import "icons/*.png"; @include all-icons-sprites; //all-後面接著的「icons」代表著是資料夾名稱 
//效果，自动将小的图标变成精灵图
.icons-sprite, .icons-facebook, .icons-twitter, .icons-yahoo { background: url('icons-s0859518ac7.png') no-repeat; } .icons-facebook { background-position: 0 0; } .icons-twitter { background-position: 0 -32px; } .icons-yahoo { background-position: 0 -64px; } 
```
### 动画	
```
@include keyframes("spin"){
  form{ width: 0px;}
  to{ width: 100px;}
}
编译后  
@-moz-keyframes spin { form { width: 0px; }
  to { width: 100px; } }
@-webkit-keyframes spin { form { width: 0px; }
  to { width: 100px; } }
@keyframes spin { form { width: 0px; }
  to { width: 100px; } }
  //使用
   @include  animation(spin .5s forwards);
```
