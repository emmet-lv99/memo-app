<template>
  <div class="ground">
    <header-comp />
    <div>Content</div>
    <footer-comp />
  </div>
</template>

<script>
import HeaderComp from './HeaderComp.vue'
import footerComp from './FooterComp.vue'
export default {
  components: { HeaderComp, footerComp },
}
</script>

<style lang="scss" scoped>
//
</style>
