<template>
  <select
  v-model="modelValue"
  @change="updateChange"
  >
    <option disabled value="">выберите золупу</option>
    <option
        v-for="option in options"
        :key="option.value"
        :value="option.value"
    >{{ option.name }}</option>
  </select>
</template>

<script>
export default {
  props:{
    modelValue:{
      type: String
    },
    options:{
      type: Array,
      default: () => []
    }
  },
  methods:{
    updateChange(event){
      this.$emit('update:modelValue', event.target.value)
    }
  }
}
</script>

<style scoped>

</style>