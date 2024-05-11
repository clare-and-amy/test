vite+vue3
```
yarn create vite my-vue-app --template vue
```

### 模板 component (defineProps, defineEmits)
[参考官方](https://cn.vuejs.org/guide/components/props.html)
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


### Element-plus 验证
```
<el-form :model="form" :rules="rules" ref="form">
  <el-form-item label="用户名" prop="username">这里其实也可以绑定rules.username</el-form-item>
</el-form>

<script setup>
const form = ref(null)
const form = reactive({
  username: '',
})
const rules = {[
  username: {
    required: true,
      message: "密码必填",
      trigger: "blur",
  }
]}


// 保存的时候验证
const save = () => {
  refForm.value.validate((valid) => {
    if(valid === false) {
      ElMessage({
        type: "error",
        message: "请填写完整",
      });
    }
  });
}
</script>
```

### watch 监听
```
import { watch } from 'vue';

// 监听多个
watch(() => [props.images], (newValue, oldValue) =>{
    data.selected = newValue[0];
}, { immediate: true, deep: true })
```

### promise
[掘金](https://juejin.cn/post/7011755708496478215)
[MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise)