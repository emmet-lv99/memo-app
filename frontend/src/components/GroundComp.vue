<template>
  <div class="ground">
    <header-comp />
    <memo-comp />
    <footer-comp />
  </div>
</template>

<script>
import HeaderComp from './HeaderComp.vue'
import MemoComp from './MemoComp.vue'
import footerComp from './FooterComp.vue'
export default {
  components: { HeaderComp, footerComp, MemoComp },
}
</script>

<style lang="scss" scoped>
//
</style>
