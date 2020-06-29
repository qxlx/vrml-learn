> 考试采取主观题加答辩的形式。3道主观题（1道论述，两道编程）。答辩4-5分钟，自己手机录制，关于这3题（主要是两道编程题）的解题思路与自己的想法。
>
> 复习内容就是VRML的编程，包括素材调用，坐标系变换，插补器，传感器，脚本节点。两道辩证题肯定会涉及到这些内容。

### 颜色 

1 0 0 红色 

0 1 0 绿色

0 0 1 蓝色

0 0 0 黑色

1 1 1 白色

1 1 0 黄色

0 1 1 蓝绿





| 角  度 | **0** | **30**    | **45**    | **60**    | **90**    | **120**   | **135**   | **150**   | **180**   |
| ------ | ----- | --------- | --------- | --------- | --------- | --------- | --------- | --------- | --------- |
| 弧  度 | **0** | **0.523** | **0.785** | **1.047** | **1.571** | **2.094** | **2.356** | **2.618** | **3.141** |

## Part1

1.试述典型的虚拟现实系统的工作原理（即工作流程）。

> VR的工作原理 一般来说分三个步骤进行信息的处理，第一，必须确保用户在激活交互设备，这样才能保证信息的输入是没有问题的。第二，从用户佩戴的终端设备中获取到数据后，传输到响应的数据识别系统 比如 对于话筒来说，进行语音识别。对于耳机来说三维声音的处理。以及头部肢体的动作作出数据采集。第三，也就说最重要的一点， 将分析后的数据存储在虚拟数据库，操作系统对数据进行分析作出相应的反馈。

2.简述一下VRML的组成要素

> VRML组成要素分为四点
>
> 1. 节点和域
>
> 	节点是VRML文件中最基本也是最核心的组成部分，单个节点可扫码造型，颜色，光照，试点 传感器等。而节点的组成有域名 域值 以及域值类型
>
> 2. 事件和路由
>
> 	事件的接口类型由事件入口 和 事件出口两种。
>
> 3. 脚本
>
> 4. 原型



## Part2

### 画一个默认的红色圆柱体

```java
# 画一个默认的红色圆柱体
Shape {
	appearance Appearance {material Material {diffuseColor 1 0 0}}
	geometry	Cylinder {}
}
```

### 画一个底面半径为1，高度为3的黄色圆锥体

```
# 画一个底面半径为1，高度为3的黄色圆锥体
Shape {
	appearance Appearance {material Material {diffuseColor 1 1 0}}
	geometry Cone {
		bottomRadius  1
		height  3
	}
}
```

### 画一个边长为2的偏紫色（颜色大概对就可以）立方体

```
Shape {
	appearance Appearance {material Material {diffuseColor 1 0 1}}
	geometry Box { size 2.0 2.0 2.0}
}
```

## Part3

### 由线集画出的四棱锥的轮廓线赋予单一的蓝色

```VRML
Shape {

	geometry IndexedLineSet	{
		coord Coordinate {
			point [
				0 3 0
				-1 0 0
				0 0 -1
				1 0 0 
				0 0 1
			]
		}

		colorIndex [
			0 1 -1
			0 4 -1
			0 3 -1
			0 2 -1
			1 2 3 4 1 -1
		]

		color Color	{
			color [
				0 0 1
				0 0 1
				0 0 1
				0 0 1
			]
		}
		coordIndex [0 1 2 3 4 ]
		colorPerVertex FALSE
	}
}
```

### **由线集画出的四棱锥的每条轮廓线赋予渐变颜色的效果。** 





### **由面集构造的四棱锥每个面赋予颜色渐变的效果**

```

```

### **三个透明度不同的红色正方体，中间穿过一根黄色的棍子，观察其可见度**

```
#VRML V2.0 utf8

Shape {
	appearance Appearance {material Material {diffuseColor 1 0 0 transparency 0.4}}
	geometry Box {size  1.0 1.0 1.0}
}


Transform {
	translation	2 0 0
	children [
		Shape {
			appearance Appearance {material Material {diffuseColor  1 0 0 transparency  0.3} }
			geometry Box {size  1.0 1.0 1.0}
		}
		Transform {
		
			translation	 3 0 0
			children [
				Shape {
					appearance Appearance {material Material {diffuseColor 1 0 0 transparency  0.2}}
					geometry Box {size 1.0 1.0 1.0 }
				}
				Transform {
					translation	 -3 0 0
					scale 1 1 1 
					rotation 0 0 1 1.571
					children [Shape {
						appearance Appearance {material Material {diffuseColor  1 1 0}}
						geometry Cylinder {radius 0.3 height 8}
					}]
				}
			]
		}
	]
}
```

绘制发光效果不同的三行三列球体，同样是黄色，从上到下一到三行分别设置为diffuseColor、emissiveColor以及同时设置二者为黄色，观察球体的发光效果





绘制一个米字造型（运用Transform节点的逐级嵌套实现）



## 自己code

四棱锥

```java
Shape {

	appearance  Appearance {
		material Material {
			emissiveColor 1.0 1.0 1.0
		}
	}

	geometry IndexedLineSet	{
		coord Coordinate {
			point [
				0.0 1.0 0.0  // x y z
				1.0 0.0 1.0
				1.0 0.0 -1.0
				-1.0 0.0 -1.0
				-1.0 0.0 1.0
			]
		}
		coordIndex [
			0 1 -1,
			0 2 -1,
			0 3 -1,
			0 4 -1,
			1 2 3 4 1 -1
		]
	}
}
```

