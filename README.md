> 组件依赖 view， 请确保已安装

## 维护者
kk

## 使用说明
该组件依赖[kfc-k2transfer](https://github.com/k2jf/kfc-k2transfer)组件，使用时需要将两个组件一起安装

```bash

# 克隆 kfc-k2transfer 组件到当前项目components中
git remote add -f kfc-k2transfer git@github.com:k2jf/kfc-k2transfer.git
git subtree add -P src/components/kfc-k2transfer kfc-k2transfer master --squash
# 克隆 kfc-field-selection 组件到当前项目components中
git remote add -f kfc-field-selection git@github.com:k2jf/kfc-field-selection.git
git subtree add -P src/components/kfc-field-selection kfc-field-selection master --squash
# 检查一下是否成功连接远程库 kfc-field-selection
git remote -vv
```




## 使用示例：
```vue
<template>
  <div>
    <FieldSelection @on-field-select-change="handleChange" />
    <FieldSelectedButton @on-ok="handleOk" />
  </div>
</template>
<script>
import { FieldSelection, FieldSelectedButton } from '@/components/kfc-field-selection'

export default {
  components: {
    FieldSelection,
    FieldSelectedButton
  },
  methods: {
    handleChange (selectedFields) {
      // ...
    },
    handleOk (selectedFields) {
     // ...
    }
  }
}
</script>

```
## API

| 属性                    | 说明                           | 类型                 | 默认值        |
| ----------------------- | ------------------------------ | -------------------- | ------------- |
| fieldType               | 数据类型                       | String               | 'gw_scada_7s' |
| @on-field-select-change | 选项在两栏之间转移时的回调函数 | Func(selectedFields) | -             |
| @on-ok                  | 弹框确认时的回调               | Func(selectedFields) | -             |