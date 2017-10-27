# vue-font
有关vue引用Font-Awesome及用阿里的iconfont

# Font-Awesome的使用：

在vue-cli脚手架中安装Font-Awesome<br>
npm install font-awesome

在main.js里添加<br>
```import 'font-awesome/css/font-awesome.css'```

在组件中调用<br>
```<i class="fa fa-weixin"></i>```

查看所需图标的class值<br>
http://fontawesome.dashgame.com/#new

利用阿里iconfont来生成自己的图标库http://iconfont.cn/home/index<br>

用阿里iconfont把本地的icon图标上传，并添加到自己的项目中，下载这个项目，该项目有iconfont.js这个文件，把它复制到vue项目中的assets中。<br>

用symbol引用的方法<br>

main.js:<br>
```import './assets/iconfont'//引入iconfont.js```

封装一个icon.vue组件：<br>
icon.vue
```
<template>
  <svg :class="iconStyle" aria-hidden="true">
    <use :xlink:href="iconName"></use>
  </svg>
</template>

<script>
  export default {
    name: 'icon',
    props: {
      iconClass: {
        type: String,
        required: true
      },
      iconStyle: String
    },
    computed: {
      iconName() {
        return `#icon-${this.iconClass}`
      }
    }
  }
</script>

<style>
// 自由定义大小
.small{
  width: 1em;
  height: 1em;
}
.normal{
  width: 2em;
  height: 2em;
}
.large{
  width: 3em;
  height: 3em;
}
</style>
```
组件中使用：
demo.vue
```
<template>
	<div class="home">
    <icon icon-style="style1 small" icon-class="icon"></icon>
    <!-- style1为icon样式，name为icon名字 -->
	</div>
</template>

<script>
  import icon from '@/components/icon.vue'
  export default {
    components: {
      'icon':icon
    }
  }
</script>

<style scoped>
.style1{
  width: 5em; 
  height: 5em;
  vertical-align: -0.15em;
  fill: #bfcbd9;
  overflow: hidden;
}
</style>
```
