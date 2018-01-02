# Angularjs / IE11 /  html style="width:{{lengthValue}}/ ng-style


## 关键字
Angularjs IE11 html style="width:{{lengthValue}}
    
## 背景
Angularjs + IE11+ htm中 style="width:{{lengthValue}}"
    
## 现象
html 中style的 :{{lengthValue}}在chrome中正确赋值，在IE11中无法识别
    
## 解决方案
1.使用ng-style替代style 
  > 将 style="width:{{lengthValue}}" 换成  ng-style="getLength()"
  
2.在getLength函数中赋值
  > $scope.getLength=function(){
    return { width: $scope.lengthValue };
  }
  
  
## 扩展

### ng-style 和 ng-class

#### ng-style
- ng-style 指令为 HTML 元素添加 style 属性。
- ng-style 属性值必须是对象，表达式返回的也是对象。
- 对象由 CSS 属性和值组成，即 key=>value 对。


#### ng-class
- ng-class 指令用于给 HTML 元素动态绑定一个或多个 CSS 类。
- ng-class 指令的值可以是字符串，对象，或一个数组。
 - 如果是字符串，多个类名使用空格分隔。
 - 如果是对象，需要使用 key-value 对，key 为你想要添加的类名，value 是一个布尔值。只有在 value 为 true 时类才会被添加。
 ```html
ng-class="{'style1': value1, 'style2':value2 }"
```
 - 如果是数组，可以由字符串或对象组合组成，数组的元素可以是字符串或对象
    
