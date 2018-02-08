# ZuJianHua
使用知乎日报API进行组件化实践
# 1. 说明
[目录结构](./pic/main.png)

1.  ZH为壳工程
2.  ZHApi网络请求api以及模型工程
3.  ZHComments长/短评论工程
4.  ZHIntent参考豆瓣的PRIntent以及Android的Intent方式实现coding中页面的跳转、传值
	
	[Intent结构](./pic/intent1.png)
	
	[Intent使用](./pic/intent2.png)
		```
		Intent 传递的数据都必须基于Serializable protocol，		且将常用的基本数据均以extension此protocol
		```
5.  ZHMain为首页的列表页

# 2.项目给运行方式
下载本项目进入ZH壳工程中pod install即可运行

####【备注】本实例采用pod的本地加载方式

```
	pod '组件名称', :path=>'组件工程路径'
```

```
	pod 'library name', :path=>'local component project path'

```
# 3.预览
# 4.所得
### 1.常用的git操作
		之前一直感觉git很简单，使用才知道会遇到很多意想不到的事情，锻炼了git的操作技能，虽然依然不是随心所欲的那么熟练，但是能够知道什么时候使用是么方式来控制
### 2.pod中使用dependency的相互依赖
		创建了ZH的壳工程之后，创建了ZHIntent和ZHApi，之后的组件需要依赖于此两项，而组件项目可以使用，引入壳工程失败，最后发现是podspec中没有声明dependency
### 3.注意iOS的版本问题
		组件库基于开发的版本要统一，由于创建的项目会基于Xcode默认罪行的iOS版本，集成中经常忽略此而出错
### 4.关于xib 资源文件的加载问题
		1. 创建UIViewController时伴随着xib的问题
		2. 加载cell时使用xib
		3. 加载本地资源文件
		对于controller默认的情况会匹配对应同名的xib，cell加载会使用绑定的，资源使用 Bundle.main，但是这个在组件中会出问题，因为集成中 Bundle.main已经不是组件工程了而是壳工程所以你是找不到对应的资源文件的
### 5. pod创建的学习 [磨刀不误砍柴工：Podspec](https://guides.cocoapods.org/syntax/podspec.html#name)
### 6. mvp mvc
		1.壳工程没有使用，在ZHMain的组件工程中使用了一些，但是也不完全，感觉mvp还是很适合进行拆分的，但就是增加了class的量跳转的太多
		2. mvc就不多少了，但是对于m没有好好的使用，没有发挥其应有的业务加工处理的职责
		3. 无论是mvc还shimvp都要看个人把我，不能把c作为所有的操作容器使m丧失应有的处理业务的共能，也不要过分的进行mvp来增加文件数量，总之根据业务适当使用划分
		