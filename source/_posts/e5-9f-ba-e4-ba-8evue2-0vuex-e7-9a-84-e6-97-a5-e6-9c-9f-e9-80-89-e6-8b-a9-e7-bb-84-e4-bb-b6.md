---
title: 基于vue2.0+vuex的日期选择组件
tags:
  - jamielhf
  - jamielhf.cn
  - jamie林海峰
  - jamie简介
  - vue
  - vue2.0
  - vue2.0+vuex
  - vue日期组件
id: 252
categories:
  - javascript
  - 前端文章
date: 2016-11-26 14:46:43
---

# calendar vue日期选择组件

## 介绍

> 一个选择日期的vue组件
> 
>   基于vue2.0
> 
>   修改了之前版本依赖vuex，插件化  支持npm
> 
>   github地址 https://github.com/jamielhf/vue/tree/master/calendar
> 
>   我的博客地址 http://jamielhf.cn

## demo展示&amp;&amp;项目中的使用

在线demo地址：https://jamielhf.github.io/vue/calendar/

![](http://upload-images.jianshu.io/upload_images/3652052-623d4dc0a7d3e077.gif?imageMogr2/auto-orient/strip)
![](http://upload-images.jianshu.io/upload_images/3652052-051c7c9bc6d96b2e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 目录结构

demo 用vue-cli 的webpack-simple构建的

```
calendar
　|--dist　build生成的目录
　|--doc   展示图片
　|--src
　　　|--assets 资源
　　　|--components
　　　　　|--calendarMain    日期组件
　　　　　|--picker  滚动的子组件
     |--modules 插件的js
　　　|--css
　　　|App.vue   入口
　　　|main.js   
```

## 组件使用

> 安装

```
npm i vue2-datepick --save
```

> 初始化

```
import Calendar from 'vue2-datepick';
Vue.use(Calendar);
```

> 使用

```
   <template>;
     <div id="app" >;
       <p @click = "setDate" >;点击设置日期（默认今天）</p>;
       <p>;选中的时间{{data}}</p>;
       <p @click = "setDate2" >;设定指定的日期（2015-2-20）</p>;
       <p>;选中的时间{{data2}}</p>;

     </div>;
   </template>;

   <script>;
   import './css/style.scss'

   export default {
     name: 'app',
     data () {
       return {
           data:'',
           data2:''
       }
     },

     methods:{

      setDate(){

          this.$calendar.show({
              onOk: (date) =>;{
                 this.data = date
              }
          });

       },
       setDate2(){

           this.$calendar.show({
               year:[1925,2015],  //年份的范围,如果初始化的年份不在这个范围，会自动选最小的年份
               date:'2015-2-20',  //初始化的日期
               onOk: (date) =>;{
                   this.data2 = date
               },
               onCancel:()=>;{
                   console.log('关闭')
               }
           });

       },

     },
   }
   </script>;

```

### 版本

2.0.4 点击背景可以关闭

2.0.0 修复之前的日期没有联动的bug，重构了一次

1.0.4 更改初始化的代码