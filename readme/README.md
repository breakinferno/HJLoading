# HJLoading
---
a component of HJProject which is used to implement the loading function.

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
## 2.loading.init(yoursetting).

### Attr
There are somes attributes you can adapt:

|attr | type | default| des
:-- | :-- | :-- | :--
loadingTPLId | number | 0 | 根据此模板id加载模板(数值只能0-6）
loadingTime | number | false | 默认为用户控制停止，输入此参数可以使其以参数时间自动停止
loadingTPL | string | 'template0' | 用户自定义模板
loadingCSS | object/string | undefined | 用户自定义样式文件名称或者用户自定义样式对象
target | object/string | 'html' | loading显示目标

特别需要指出的是，如果没有传入loadingTPL，则会自动加载默认模板（0号），如果传入用户自定义模板，则组件应用传入模板。不能同时传入loadingTPLId和loadingTPL，如果自定义模板才需要传入loadingCSS属性，不然最好不用传入此参数，因为组件会自动匹配相应模板的css样式表。
### example
```javascript
  //默认模板
  loading.init({
    loadingTPLId : 1,
    target : this,
  });

  //自定义模板
  loading.init({
    loadingTPL : '<div class="special"></div>',
    target : '.yourtarget',
    loadingTime : 4000,
    loadingCSS: 'your-css-file-name',
 });
 
 //或者
   loading.init({
    loadingTPL : '<div class="special"></div>',
    target : '.yourtarget',
    loadingTime : 4000,
    loadingCSS: {
      background-color : red,
    },
 });
```

## 3.Loading.start()

启动loading

### example
```javascript
  loading.start();
```

## 4.Loading.stop()

停止loading操作，默认用户自己调用此函数，如若存在loadingTime参数，则自动以参数停止
### example
```javascript
  loading.stop();
```
