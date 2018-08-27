
## 原作者已不再更新，故此fork一个出来，记录一些坑

### 一、es3中，保留字/关键字不能直接作为对象属性，该项目使用了es6-promise，在ie8-下会报错：缺少标识符
解决办法：引入es3ify，或者在node_modules\es6-promise\下搜索“prototype.catch”、“prototype.finally”，手动修改为“prototype['catch']”、“prototype['finally']”

### 二、ie7下，对象最后一个元素后面不能有逗号

### 二、升级avalon，会导致页面卡死，按照部分网友的说法，可将组件的<xmp></xmp>标签改为<wbr/>；因为项目很多组件用到了slot插槽元素，所以该方法不现实

### 三、avalon2.2.5版本表单验证原理：
扫描有ms-validate属性的form元素，将其中需要验证的表单元素搜集到validator.field[]，后续submit操作触发onValidateAll时，只会验证该数组里的元素。
这意味着利用路由新载入的表单不会被验证，最新版的avalon框架已解决该问题，将avalon2.2.5的 6722 ~ 6943 行替换为最新版即可。
