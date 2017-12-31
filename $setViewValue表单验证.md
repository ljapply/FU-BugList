# Angularjs /$setViewValue /$render / 表单验证不能自动清空

## 关键字
Angularjs   $setViewValue   $render  表单验证部自动清空
    
## 背景
Angularjs  数据格式化  自定义命令不更新
    
## 试用场景：
- 数据格式化: input输入内容格式化后再填充
   例如：
   - 用户输出0.3.  ，失去光标，格式化成0.3填充 
   - 用户输入的内容，失去光标，加密后填充
- 表单验证触发：Angularjs自定义的表单验证不能及时触发
   例如：
    - 表单内容不是用户输入，而是弹出自动填充，此时不能触发自定义的Angularjs表单验证指令
   - Angularjs uib-typeahead 不能自动触发表单验证
 - 表单验证clean：对话框关闭或者reset后，表单验证内容不能清空
	例如：
	输入IP错误--点击取消按钮--对话框关闭--再次打开--IP错误的表单验证依旧存在
 
## 解决方案
```javascript
$scope.onSelectItem = function($item){
        var inputItem = angular.element(document.querySelector('#inputItem'));
        var ngModelCtrl = inputUser.controller('ngModel');
        ngModelCtrl.$setViewValue($item.Name);
        ngModelCtrl.$render();
    };
```    
## 遗留问题
### 问题1
如果input少的话，可以这样一个个的使用，如果input的内容很多，将怎么优化呢？如上场景3
尝试过使用
```javascript
	$scope.myForm.$setPristine();
     $scope.myform.$setUntouched();
```
无效
