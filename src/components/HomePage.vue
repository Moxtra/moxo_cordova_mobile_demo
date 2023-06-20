<template>
    <h1>Welcome to Moxo Demo!</h1>
    <h2>Click icon at bottom right to start login</h2>
    <el-button id="icon" type="primary" @click="moxoLogin" :loading="isLoading" circle />
</template>
<script>

export default {
  name: 'HomePage',
  data() {
    return {
        isMoxoLogedIn: false,
        isLoading: false,
        domain: process.env.VUE_APP_DOMAIN,
        client_id: process.env.VUE_APP_CLIENT_ID,
        client_secret: process.env.VUE_APP_CLIENT_SECRET,
        org_id: process.env.VUE_APP_ORG_ID,
        email: process.env.VUE_APP_EMAIL,
        unique_id: process.env.VUE_APP_UNIQUE_ID
    }
  },
  methods: {
    moxoLogin() {
      if (this.isMoxoLogedIn) {
        window.Moxtra.showMEPWindow();
      } else {
        //start login 
        this.isLoading = true;
        var token = this.getAccessToken();
        window.Moxtra.setupDomain(this.domain);
        window.Moxtra.linkWithAccessToken(token,this.loginSuccess,this.loginFailed);
      }
    },
    getAccessToken() {
      var xmlHttp = new XMLHttpRequest();
      var tokenDomain = 'https://' + this.domain + "/v1/core/oauth/token";
      var body = {
        client_id: this.client_id,
        client_secret: this.client_secret,
        org_id: this.org_id
      } 
      if (this.unique_id != undefined) {
        body.unique_id = this.unique_id;
      } else {
        body.email = this.email;
      }
      xmlHttp.open( "POST", tokenDomain, false );
      xmlHttp.setRequestHeader("Content-Type", "application/json;charset=UTF-8");
      xmlHttp.send( JSON.stringify(body) );
      if (xmlHttp.status == 200) {
        var result = JSON.parse(xmlHttp.responseText);
        return result.access_token;
      }
      return "";
    },
    loginSuccess() {
      this.isMoxoLogedIn = true;
      this.isLoading = false;
      window.Moxtra.showMEPWindow();
    },
    loginFailed(error) {
      this.isLoading = false;
      console.log("login failed" + error);
    }
  }
}
</script>

<style>
#icon {
    position: fixed;
    bottom: 16px;
    right: 16px;
    background-size: 60px 60px;
    background-image:url('@/assets/logo.png');
    margin:0 auto;
    width: 60px;
    height: 60px;
}
</style>