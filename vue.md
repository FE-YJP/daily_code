### vue-cli2打包不打包map文件  
#### 只需把config/index.js中的productionSourceMap: true改为productionSourceMap: false即可  
### vue打包优化  
#### https://segmentfault.com/a/1190000012249890
### 解决数据层级太多更不能实时更新视图问题 this.$forceUpdate();
#### 因为数据层次太多，render函数没有自动更新，需手动强制刷新。
### 如何配置404页面详细
https://juejin.im/post/5b019ad7f265da0ba567d259
### 404页面的设置简单配置
#### 如果SPA的路由表是固定的，那么配置404页面就变得非常的简单。只需要在路由表中添加一个路径为404的路由，同时在路由表的最底部配置一个路径为*的路由，重定向至404路由即可。
#### （由于路由表是由上至下匹配的，一定要将任意匹配规则至于最底部，否则至于此路由规则下的路由将全部跳转至404，无法正确匹配。）
#### 
```
// router.js  

export default new Router({  

  mode: 'history',  
  
  routes: [  
  
    // ...  
    
    {  
    
      name: '404',  
      
      path: '/404',  
      
      component: () => import('@/views/notFound.vue')  
      
    },  
    
    {  
    
      path: '*',    // 此处需特别注意至于最底部  
      
      redirect: '/404'  
      
    }  
    
  ],  
  
})  

```
### vue轮播插件vue-awesom-swiper bug
在项目中使用vue-awesome-swiper如果loop和autoplay总是出现各种问题,第一次加载的时候,轮播是不动的,需要重新加载一下swiper才会轮播
//轮播设置
```
swiperOption: {
　　direction: 'vertical',
　　observer:true,//修改swiper自己或子元素时，自动初始化swiper 
　　observeParents:true,//修改swiper的父元素时，自动初始化swiper 
　　loop:true,
　　autoplay: {
　　　　delay: 2000,
　　disableOnInteraction: false
　　}
}
```
需要添加上两个属性,这样达到一个初始化swiper的目的
observer:true,//修改swiper自己或子元素时，自动初始化swiper 
observeParents:true,//修改swiper的父元素时，自动初始化swiper 

### vue中使用swiper-slide时，循环轮播失效？

loop  设置为true 则开启loop模式。loop模式：会在原本slide前后复制若干个slide(默认一个)并在合适

的时候切换，让Swiper看起来是循环的。 
loop模式在与free模式同用时会产生抖动，因为free模式下没有复制slide的时间点。

在原本基础上复制若干个slide，可是在vue的v-for中时，异步加载的数据都还没有返回时，就先加载了Swiper组件并复制了sliper

解决办法：利用v-if的属性，v-if=加载列表.length，确保异步加载的数据已经返回后，再加载swiper组件
