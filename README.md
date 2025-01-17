# 前言

> [jinzhe 大佬的 vue-calendar](https://github.com/jinzhe/vue-calendar)

## 食用方式

### 安装

```bash
npm install vue-calendar-h5-tf

# or

cnpm install vue-calendar-h5-tf
```

### 普通使用

```vue
<template>
  <div id="app">
    <h5-calendar></h5-calendar>
  </div>
</template>

<script>
// 局部引入
import H5Calendar  from 'vue-calendar-h5-tf'
export default {
  name: 'App',
  components: { H5Calendar }
};

// 全局引入
import H5Calendar from 'vue-calendar-h5-tf'
Vue.use(H5Calendar)
</script>
```

## Dome

```vue
<template>
  <div>
    <div class="calendardome">
      <h5>原作者版本(加了滑动切换)</h5>
      <H5Calendar lunar :touchthreshold="50"/>
    </div>
    <div class="calendardome">
      <h5>纯展示版本</h5>
      <H5Calendar
        lunar
        :touchthreshold="50"
        :controllable="false"
        versions="juli"
        isshowtoday
      />
    </div>
  </div>
</template>

<script>
import H5Calendar from "vue-calendar-h5-tf";
export default {
  components: { H5Calendar }
};
</script>

<style scoped>
.calendardome {
  padding: 0 22px;
}
</style>
```



```vue
<template>
  <div class="calendardome">
    <H5Calendar>
      <template #header="{ date, data }">
        {{ date }}
        {{ data }}
			</template>
			<template #footer="{ date, data }">
        {{ date }}
        {{ data }}
			</template>
  	</H5Calendar>
    </div>
</template>

<script>
import H5Calendar from "vue-calendar-h5-tf";
export default {
  components: { H5Calendar }
};
</script>

<style scoped>
.calendardome {
  padding: 0 22px;
}
</style>
```



## 演示网站

###### 可以到[http://www.yi-school.top](http://www.yi-school.top/#/)查看效果演示

## 默认配置

关于配置信息，请查看源文档，感谢原作者 jinzhe 大佬的[vue-calendar](https://github.com/jinzhe/vue-calendar)  
这里这是做了简单的汇总
| 名称 | 功能 | 默认值 |
| :--- | :--- | :--- |
| value | 日历默认值 | [] |
| begin | 限制开始选择日期 | [] |
| end | 限制结束选择日期 | [] |
| range | 你可以选择一个时间段 | false |
| zero | 日期 0 | false |
| lunar | 显示中国农历 | false |
| weeks | 根据系统语言变化或自定义星期显示 | 根据系统选择显示(星期一 or Mon)等 |
| months | 根据系统语言变化或自定义月份显示 | 根据系统选择显示(一月 or January)等 |
| events | 自定义日历事件 | {} |
| multi | 多选模式 | false |
| zero | 是否小于 10 补零 | false |
| disabled | 需要屏蔽的日期 | [] |
| **以上原作者配置,以下新增配置** |
| controllable | 是否可以点击(纯展示建议为 false) | true |
| versions | 显示版本(为空则原作者版本,'juli'则纯展示版本) | '' |
| isshowtoday | 是否在日期上标注今天 | false |
| touchthreshold | 滑动切换的阈值(number 类型 0 为不开启) | 0 |
| collapse | 开启折叠功能 | false |
| **增加支持slot功能** |
| slot 名称 | 位置 | v-slot 携带数据 |
| header | 头部 | { date, data } |
| footer | 尾部 | { date, data } |
| collapse | 折叠 | { collapse } |

## 版本

### 1.0.0

完成优化并修复一些Issues

## Issues修复记录和说明

### [原作者Issues#83](https://github.com/jinzhe/vue-calendar/issues/83)
额...这个...好吧,为了后期的方便维护或者版本的迭代开发,还是有需要npm模块引入的存在与必要,于是就更新到npm模块上啦!地址:npm：[https://www.npmjs.com/package/vue-calendar-h5](https://www.npmjs.com/package/vue-calendar-h5)

### [原作者Issues#80](https://github.com/jinzhe/vue-calendar/issues/80)
这个其实问题不大,因为在浏览器判断不符合或者没有心仪数组的时候,作者很贴心的允许你自行传入weeks 和 months,但是为了严谨性,我还是对源码的判断修改了一下,提问者告知了有新语言包名字的存在,的确名字有些许变化,不过问题不大,大中国嘛,zh-开头肯定是跑不了,于是就改成window.navigator.language.toLowerCase().indexOf('zh') !== -1这样去判断

### [原作者Issues#65](https://github.com/jinzhe/vue-calendar/issues/65)
手机发展这么快,手势滑动则成为了刚需,好在作者的组件用了自适应,能适配pc和手机,所以在手机上能展示,必须有手机的功能,于是我加入了一个参数touchthreshold,这个是滑动的阈值,如果在屏幕的滑动距离超过这个,则会进行翻页操作,建议touchthreshold不要太小,否则可能会出现用户选择日期的时候就被滑动了,可以根据项目来,我在pc上的大小时候设置的是100,dome里面的话设置的是50

### [原作者Issues#51](https://github.com/jinzhe/vue-calendar/issues/51)
额...看了好几个Issues好像都是指向这个问题,跨月选择也是这个问题,因为我的项目不需要用到选择,于是没有深入研究,所以采用了这个Issues里面一个码友(leat14536)的改法,进行了修改,但是没有测试过,如果有问题,欢迎再提Issues给我

## 鸣谢

##### 日历组件的原作者 jinzhe

大佬的签名果然比较新颖[一位合格的前端开发者，应对视觉设计感兴趣。](https://github.com/jinzhe),感谢大佬开源了一个这么好的组件,提供了这么好看的样式,大大的节省了开发的时间!比心❤
