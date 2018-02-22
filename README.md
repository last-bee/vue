# vue
## Vue.extend构造器
### 简单介绍（Vue.extend(options)）  
```
参数：对象  
用法：使用Vue构造器，创建一个“子类”，参数是一个包含组件选项的对象，其中,data选项中必须是函数 
描述：Vue.extend返回的是一个“扩展实例构造器”，也就是预设了部分选项的Vue的实例构造器，它常常服务于Vue.component用来生成组件，可以简单理解为当在模板中遇到该组件作为标签的自定义元素时，会自动调用“扩展实例构造器”来生产组件实例，并挂在到自定义元素上  
```
### 简单举例
* 自定义无参数标签  
``` javascript
var author = Vue.extend({
    template: "<p><a :href='url'>{{author}}</a></p>",
    data : function() {
      return {
        author : 'lastbee',
        url : 'https://github.com/last-bee'
      }
    }
 });
 ```
* 对应的html如下：
``` javascript 
<author></author> 
```
* 扩展的构造器需要挂载  
``` javascript
new author().$mount('author');
```  
* 使用propsData传参
``` javascript
var author = Vue.extend({  
  template: "<p><a :href='url'>{{author}} & {{name}}</a></p>",  
  data : function() {  
    return {  
      author : 'lastbee',  
      url : 'https://github.com/last-bee'  
    }  
  },  
  props : ['name']  
}); 
new author({propsData: {name : 'change_name'}}).$mount('#author'); ```
```
### 挂载在普通标签上  
返回的扩展实例构造器的方式和上面还是一样的，只是html里不再是自定义标签，而是一个普通标签，比如div
 ``` javascript 
 <div id="author"></div> 
 ```  
 ``` javascript
 new author().$mount('author'); 
 ```
### 其实对于同一个扩展构造器而言，它的每一个实例其实是可以挂载到不同的标签上的，比如我可以这样
``` javascript
new author().$mount('#author');
```
``` javascript 
new author().$mount('author'); 
```
* 这两个标签的内容会一同显示，结果一样
```
 [vue官方文档](https://cn.vuejs.org/v2/api/#Vue-extend)
 [node-jsonp链接](https://www.npmjs.com/package/node-jsonp)
