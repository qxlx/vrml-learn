

# 点集

## 五个定点的四棱锥

```
Shape {
    #appearance Appearance {material  Material {diffuseColor  1 1 0}}
	geometry  PointSet { //点集
		coord Coordinate { //坐标
			point [//坐标列表 x y z
				0 3 0  # y
				0 0 -1 # Z
				1 0 0
				0 0 1 
				-1 0 0
			]
		}
	}
}
```

# 线集

## 五个定点连接成四个四棱锥题的造型

```
Shape {
    #appearance Appearance {material  Material {diffuseColor  1 1 0}}
	geometry  IndexedLineSet { 
		coord Coordinate { 
			point [
				0 3 0  # y
				0 0 -1 # Z
				1 0 0
				0 0 1 
				-1 0 0
			]
		}
		coordIndex [
			0 1 -1
			0 2 -1
			0 3 -1
			0 4 -1
			1 2 3 4 1 -1
		]
	}

}
```

