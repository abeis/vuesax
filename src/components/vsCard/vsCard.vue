<template lang="html">
  <div
    :class="{ actionable }"
    :style="{
      /* 'border-color':vsColor?/[#()]/.test(vsColor)?vsColor:`rgba(var(--${vsColor}),1)`:'rgb(255,255,255)' */
    }"
    class="vs-card"
    @click="clickCard">
    <slot/>
  </div>
</template>

<script>
export default {
  name:'VsCard',
  props:{
    vsColor:{
      type:String,
      default:'primary'
    },
    actionable:{
      type:Boolean,
      default: false
    }
  },
  methods:{
    clickCard(){
      this.$emit('vs-click')
    }
  }
}
</script>

<style lang="stylus" scoped>
  .vs-card
    width calc(100% - 10px)
    // border 1px solid rgba(0, 0, 0, 0.050);
    border-radius 8px
    box-shadow: 0 20px 40px -8px rgba(0,0,0,0.1);
    margin 5px
  .actionable
    cursor pointer
    transition-property box-shadow, transform
    transition-duration .15s
    &:hover
      transform translateY(-2px)
      box-shadow 0 18px 35px rgba(50, 50, 93, .1), 0 8px 15px rgba(0, 0, 0, .07)
</style>

<style lang="stylus"> // cannot be scoped due to inheritance
  .vs-card
    > div
      border-top-right-radius 0 !important
      border-top-left-radius 0 !important
    > div:first-child
    > div:first-child > img
      border-top-right-radius 8px !important
      border-top-left-radius 8px !important
</style>
