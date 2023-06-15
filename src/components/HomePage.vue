<template>
    <h1>Welcome to Moxo Demo!</h1>
    <h2>Click icon at bottom right to start login</h2>
    <el-button id="icon" type="primary" :click="moxoLogin" circle />
</template>
<script>

import logo from '@/assets/logo.png';
export default {
  name: 'HomePage',
  data() {
    return {
        isMoxoLogedIn: false,
        isLoading: true
    }
  },
  setup() {
    return logo
  },
  methods: {
    iconStyle() {
      let s = "width: 42px;height: 42px;align-items: center";
      return "background-size: 42px 42px;backgroundImage:url(" + logo + ");margin:0 auto;" + s;
    //   if (t == 1) {
    //     return "background-size: 42px 42px;backgroundImage:url(" + logo + ");margin:0px 16px 0px 0px;" + s;
    //   } else if (t == 2) {

    //   }
    }
  }
}
</script>

<style>
#icon {
    position: fixed;
    bottom: 16px;
    right: 16px;
    background-size: 42px 42px;
    background-image:url('@/assets/logo.png');
    margin:0 auto;
    width: 42px;
    height: 42px;
}
</style>