<template>
  <div ref="wrap">
    <slot >
      富文本添加功能
    </slot>
  </div>
</template>
<script>
export default {
  props:{
    group:{
      type: String,
      default: 'default'
    }
  },
  mounted(){
    this.$initGallery(this.$refs.wrap, this.group)
  },
  beforeDestroy() {
    this.$removeGallery(this.group);
  },
}
</script>

<style>

</style>
