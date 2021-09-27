[【官方自制】 Simulink 基础入门系列（全7P）_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1Kz4y1r7ep?spm_id_from=333.999.0.0)

## Simulink

Matlab  

Mat 矩阵

lab 实验室

Matlab

# 仿真

# 软件开发





脚本编程

【新建】【脚本】

鼠标点击一下，设立断点。

<img src="C:\Users\mqc\AppData\Roaming\Typora\typora-user-images\image-20210921215208774.png" alt="image-20210921215208774" style="zoom:50%;" />

<img src="C:\Users\mqc\AppData\Roaming\Typora\typora-user-images\image-20210921215350061.png" alt="image-20210921215350061" style="zoom:50%;" />单步运行





函数编程

【新建】【函数】

matlab 函数名需要和文件名一致（全局函数）



<img src="C:\Users\mqc\AppData\Roaming\Typora\typora-user-images\image-20210921215534654.png" alt="image-20210921215534654" style="zoom:50%;" />

内部局部函数：

<img src="C:\Users\mqc\AppData\Roaming\Typora\typora-user-images\image-20210921220259120.png" alt="image-20210921220259120" style="zoom:50%;" />

不应该让函数太大。大了之后，后续调试都很麻烦。



面对象编程   

【新建】【类】

matlab类名需要和文件名一致

~~~ matlab
classdef classname %创建类

	properties % 类属性
		property1
	end
	
	methods  % 类方法 %  方法 = 函数
		function obj = untitled ( inputArg1,inputArg2)
		
		obj.property1 = inputArg1 + inputArg2
		end
		
		function outputArg = method1 ( obj,inputArg)
		
		outputArg = obj.property1 + inputArg
		end
	end
end		
~~~



命令，搜先搜索当前文件。如果没有

<img src="C:\Users\mqc\AppData\Roaming\Typora\typora-user-images\image-20210921221320463.png" alt="image-20210921221320463" style="zoom:50%;" />

当前文件如果找不到，那么就会到搜索路径里去找

<img src="C:\Users\mqc\AppData\Roaming\Typora\typora-user-images\image-20210921221408918.png" alt="image-20210921221408918" style="zoom:50%;" />

> 添加的路径过多，可能会很慢。 

![image-20210921221607884](C:\Users\mqc\AppData\Roaming\Typora\typora-user-images\image-20210921221607884.png)

> doc 帮助文档

## Simulink

<img src="C:\Users\mqc\AppData\Roaming\Typora\typora-user-images\image-20210921224307417.png" alt="image-20210921224307417" style="zoom:50%;" />

开始页面。

blank mode 空模型

<img src="C:\Users\mqc\AppData\Roaming\Typora\typora-user-images\image-20210921224419061.png" alt="image-20210921224419061" style="zoom:50%;" />







