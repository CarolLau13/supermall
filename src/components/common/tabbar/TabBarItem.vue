<template>
  <!-- 所有的item都展示同一个图片，同一个文字 -->
  <div class="tab-bar-item" @click="itemClick">
    <div v-if="!isActive"><slot name="item-icon"></slot></div>
    <div v-else><slot name="item-icon-active"></slot></div>
    <div :style="activeStyle"><slot name="item-text"></slot></div>
  </div>
</template>

<script>
export default {
  name: "TabBarItem",
  props: {
    path: String,
    activeColor: {
      type: String,
      default: "red",
    },
  },
  data() {
    return {
      // isActive: true,
    };
  },
  computed: {
    isActive() {
      //console.log(this.path);
      //  let a='/home';
      //  let b='/cart';
      //  let result=a.indexOf(b);
      // console.log(result);

      // let result = this.$route.path.indexOf(this.path);
      // if(result == -1) {
      //   return false;
      // }
      // else{
      //   return true;
      // }

      //return this.$route.path.indexOf(this.path) !== -1;

      return this.$route.path == this.path;
    },
    activeStyle() {
      // if (this.isActive) {
      //   return { color: this.activeColor };
      // } else {
      //   return {};
      // }
      return this.isActive ? { color: this.activeColor } : {};
    },
  },
  methods: {
    itemClick() {
      this.$router.replace(this.path);
    },
  },
};
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
</style>