# HJLoading
---
a component of HJProject which is used to implement the loading function.

In this version,you just use the HJLoading object to delegate the loading behaviour.

# Install

```javascript
<script src="youdirctory/HJLoading.js"></script>
```

# Usage
## 1.initial the instance 

```javascript
    var  loading = new HJLoading('your-css-directory');
```

### exmaple
```javascript
  var loading = new HJLoading('../src/css');
```
## 2.loading.start(yoursetting).

### Attr
There are somes attributes you can adapt:

|attr | type | default| des
:-- | :-- | :-- | :--
loadingTPLId | number | 0 | 根据此模板id加载模板(数值只能0-6）
loadingTime | number | false | 默认为用户控制停止，输入此参数可以使其以参数时间自动停止
loadingTPL | string | 'template0' | 用户自定义模板
loadingCSS | object/string | undefined | 用户自定义样式文件名称或者用户自定义样式对象
target | object/string | 'html' | loading显示目标
loadingId | string | 'HJLoading0' | 如果你想准确的控制某loading行为则必须需要此属性
loadingScale | number | 0.5 | 用于调整loading大小.默认为容器的一半

特别需要指出的是，如果没有传入loadingTPL，则会自动加载默认模板（0号），如果传入用户自定义模板，则组件应用传入模板。不能同时传入loadingTPLId和loadingTPL，如果自定义模板才需要传入loadingCSS属性，不然最好不用传入此参数，因为组件会自动匹配相应模板的css样式表。

还要注意的是：如果你自动停止loading则可以不用传递loadingId，如果你想手动人为控制行为，则必须传入loadingId属性。
### example
```javascript
  //默认模板
  HJLoading.start({
    loadingTPLId : 1,
    target : this,
    loadingId : 'self'
  });

  setTimeout(function(){
    loading.stop('self');
  },3000);

  //自定义模板
  HJLoading.start({
    loadingTPL : '<div class="special"></div>',
    target : '.yourtarget',
    loadingCSS: 'your-css-file-name',
    loadingId : 'justify'
 });

   setTimeout(function(){
    loading.stop('justify');
  },3000);
 
 //或者
   HJLoading.start({
    loadingTPL : '<div class="special"></div>',
    target : '.yourtarget',
    loadingTime : 4000,
    loadingCSS: {
      background-color : red,
    },
 });
```


## 3.Loading.stop('your-loadingId')

停止loading操作，默认用户自己调用此函数，如若存在loadingTime参数，则自动以参数停止
### example
```javascript
  HJLoading.stop('self');
```
