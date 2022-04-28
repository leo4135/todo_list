<template>
  <div @click="hideDialog" class="dialog" v-if="show">
    <div @click.stop class="dialog__body">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    show: Boolean
  },
  methods: {
    hideDialog(){
      this.$emit('update:show', false)
    }
  }
}
</script>

<style scoped>
.dialog {
  left:0;
  right: 0;
  bottom: 0;
  top:0;
  display: flex;
  position: fixed;
  background: rgba(0,0,0, 0.5);
}
.dialog__body {
  margin: auto;
  width: 400px;
  height: 200px;
  background: white;
}
</style>