<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Vue](#vue)
  - [生命周期及其函数作用](#%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F%E5%8F%8A%E5%85%B6%E5%87%BD%E6%95%B0%E4%BD%9C%E7%94%A8)
  - [组件间通讯的手段](#%E7%BB%84%E4%BB%B6%E9%97%B4%E9%80%9A%E8%AE%AF%E7%9A%84%E6%89%8B%E6%AE%B5)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Vue

## 生命周期及其函数作用

![生命周期图例](./lifecycle.png)

* beforeCreate 初始化实例$options;初始化生命周期;初始化事件;初始化render函数;在实例初始化之后，数据观测 (data observer) 和 event/watcher 事件配置之前被调用。
* created 实例已创建;数据监测已激活;实例参数已注入;在这一步，实例已完成以下的配置：数据观测 (data observer)，property 和方法的运算，watch/event 事件回调。然而，挂载阶段还没开始，$el property 目前尚不可用。
* beforeMount 已存在虚拟DOM,已挂载DOM模板;尚未完成插值替换;
* mounted 渲染完成页面,完成插值替换,组件实例创建完成;
* beforeUpdate 数据已发生改变,但未同步至页面;
* updated 数据已更新完成,页面已同步更新;
* beforeDestroy 实例销毁前触发,此时实例属性均存在未被销毁(被keep-alive组件包裹的离开页面无法触发,需手动调用$destroy触发卸载)
* destroyed 实例销毁后触发,实例属性均无法操作(被keep-alive组件包裹的离开页面无法触发,需手动调用$destroy触发卸载)

## 组件间通讯的手段

* props/emit
* provides/inject
* vuex (主要用来非直系跨层级组件间的通信)
