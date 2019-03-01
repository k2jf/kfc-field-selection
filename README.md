> 组件依赖 view， 请确保已安装

将下面配置加入 `package.json >> dependencies` 中

`"kfc-k2transfer": "git+https://github.com/k2jf/kfc-k2transfer.git"`

然后执行 `npm install kfc-k2transfer` 安装插件

## API

| 属性                    | 说明                           | 类型                 | 默认值        |
| ----------------------- | ------------------------------ | -------------------- | ------------- |
| fieldType               | 数据类型                       | String               | 'gw_scada_7s' |
| @on-field-select-change | 选项在两栏之间转移时的回调函数 | Func(selectedFields) | -             |
|                         |                                |                      |               |



## 使用示例：
```vue
<template>
  <div>
    <FieldSelection @on-field-select-change="handleChange" />
    <div class="btn-demo">
      <h2>按钮方式</h2>
      <FieldSelectedButton @on-ok="handleOk" />
    </div>
  </div>
</template>
<script>
import { FieldSelection, FieldSelectedButton } from '@/components/kfc-field-selection'

export default {
  name: 'Another',
  components: {
    FieldSelection,
    FieldSelectedButton
  },
  data () {
    return {

    }
  },
  methods: {
    handleChange (selectedFields) {
      console.log('%c==================', 'color:red')
      console.log('%c穿梭框已选字段', 'color:red;font-size: 16px;font-weight:bold;')
      console.table(selectedFields)
      console.log('%c==================', 'color:red')
    },
    handleOk (selectedFields) {
      console.log('%c==================', 'color:blue')
      console.log('%c按钮已选字段', 'color:blue;font-size: 16px;font-weight:bold;')
      console.table(selectedFields)
      console.log('%c==================', 'color:blue')
    }
  }
}
</script>
<style scoped>
.btn-demo {
  width: 800px;
  height: 100px;
  border: 1px solid rgb(76, 167, 147);
  border-radius: 6px;
  margin: 0 auto;
  text-align: center;
}
h2 {
  height: 40px;
  line-height: 40px;
}
</style>

```
