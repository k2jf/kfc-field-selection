<template>
  <div class="transfer-demo">
    <K2Transfer
      :data="fieldData"
      filterable
      :style="{width: '702px', margin: '0 auto'}"
      :list-style="{height: '400px', width: '300px'}"
      :target-keys="targetKeys"
      :titles="['未选字段', '已选字段']"
      :operations="['去除','选取']"
      @on-change="handleChange"
      @on-dblclick="handleChange">
    </K2Transfer>
  </div>
</template>
<script>
import K2Transfer from 'kfc-k2transfer'

export default {
  name: 'FieldSelection',
  components: {
    K2Transfer
  },
  props: {
    fieldType: {
      type: String,
      default: 'gw_scada_7s'
    }
  },
  data () {
    return {
      fields: [],
      targetKeys: []
    }
  },
  computed: {
    fieldData () {
      return this.fields.map(f => {
        return {
          key: f.systemId.toString(),
          label: f.name
        }
      })
    }
  },
  mounted () {
    this.$axios.get('/data-service/v2/field-groups').then(res => {
      console.log(res)
      // this.fields = res
    })
  },
  methods: {
    handleChange (newTargetKeys) {
      this.targetKeys = newTargetKeys
      const selectedFeilds = this.fields.filter(
        f => newTargetKeys.includes(f.systemId.toString())
      )
      this.$emit('on-field-select-change', selectedFeilds)
    }
  }
}
</script>
<style lang="scss" scoped>
.transfer-demo {
  padding: 30px;
}
</style>
