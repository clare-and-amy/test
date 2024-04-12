vite+vue3
```
yarn create vite my-vue-app --template vue
```

### 模板 component
```
# 父页面 index.vue
<template>
    <box :notice="'hello'" @mmmchange="mmmchange"></box>
</template>
<script setup>
import box as box from box.vue
const mmmchange = (e) => {
    console.log(e)
} 
</script>
```

```
# 组件 box.vue
<template>
    <div @click="add">{{props.notice}}</div>
</template>
<script setup>
import { defineProps, defineEmits } from 'vue';

// 接受到父页面传递的参数，一下有两种接受方式
const props = defineProps({
  notice: String,
  multiple: {
    type: Boolean,
    default: false,
  },
});

const emits = defineEmits(["mmmchange"]);

const add = () => {
    emits("mmmchange", "test");
}
</script>
```
更多用法 ： [参考链接](https://juejin.cn/post/7197970175479611451)