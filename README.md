# vue3 + vite

拉取现有的 [vue-jsmind](https://github.com/chentoday/vue-jsmind) 

思路：

* 创建Props组件显示属性，实现属性的增删查改
* 给jmnode节点绑定mouseover事件
* 父子组件通过props参数传递进行通讯，确定Prop组件的显示位置、显示状态
* ddl前未完成需求4，设想获取结点的层级，将各个层级的属性存入对象数组，在触发mouseover事件时寻找映射并显示。
# 预览

终端运行
```
yarn 
yarn dev
```
