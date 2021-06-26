<template>
<!--  <div class="tab-bar-item"><img src="../../assets/img/课程.png" alt=""><div>首页</div></div>-->
<!--  <div class="tab-bar-item"><img src="../../assets/img/课程.png" alt=""><div>分类</div></div>-->
<!--  <div class="tab-bar-item"><img src="../../assets/img/课程.png" alt=""><div>购物车</div></div>-->
<!--  <div class="tab-bar-item"><img src="../../assets/img/课程.png" alt=""><div>我的</div></div>-->
  <div class="tab-bar-item" @click="itemClick">
    <slot v-if="!isActive" name="item-icon"></slot>
    <slot v-else name="item-icon-active"></slot>
    <div :style="activeStyle"><slot name="item-text"></slot></div>
  </div>
</template>

<script>
export default {
  name: "TarBarItem",
  props: {
    path: String,
    activeColor: {
      type: String,
      default: '#333333'
    }
  },
  data() {
    return {
      // isActive : true,
    }
  },
  computed:{
    isActive() {
      return this.$route.path.indexOf(this.path) !== -1
    },
    activeStyle() {
      return this.$route.isActive ? {color: this.activeColor} : {}
    }
  },
  methods: {
    itemClick() {
      // console.log('itemCilck')
      this.$router.replace(this.path)
    }
  }
}
</script>

<style scoped>
.tab-bar-item {
  flex: 1;
  text-align: center;
  height: 49px;
  font-size: 14px;
}

.tab-bar-item img {
  width: 24px;
  height: 24px;
  margin-top: 3px;
  vertical-align: middle;
  margin-bottom: 2px;
}

/*.active {*/
/*  color: #333333;*/
/*}*/

</style>
