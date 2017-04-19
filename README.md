## BOOTSTRAPREF(bootstrap类说明)

* 对于bootstarp进行详细类介绍，是一个实用的参考手册。
* 标明各个类的优先级，便于覆盖该类。

## 使用说明

* 带()的类在本less中并未被实现，需要在其他模块中调用以实现其功能。
* 优先级高于单class类会在后面标注优先级,若要覆盖该样式，其优先级必须大于等于原本类优先级。

## 分类

* mixins类
 * [utilities类-基本工具类](./mixins/utilities.md)
 * [components类-基本组建类](./mixins/components.md)
 * [skins类-颜色控制类](./mixins/skins.md)
 * [layout类-框架布局控制类](./mixins/layout.md)

## 附录-标签优先级说明

采用4位2进制表示css选择器优先级,1000>0100>0010>0000。  
 * *:0000;
 * 标签(类似:p),伪元素(类似:first-line):0001;
 * class,伪类(类似:hover),属性选择器(类似[href]):0010;
 * id选择符:0100;
 * 类末尾添加!important或内联:1000;

标签优先级说明更多参考:[我的博客](http://blog.csdn.net/happy05abc/article/details/51939848).

	
