<template>
  <div class="home">
    <div class="container col-12 col-sm-6 col-lg-4">
      <bot-list />
    </div>
    <hr />
    <!-- <img alt="phxstra logo" src="../assets/phxstra-logo.png" width="450px" class="my-5" /> -->
    <div alt="phxstra logo" class="logo-svg my-5 mx-auto" />
    <div>
      <h1>Welcome to the phxstra UI</h1>
    </div>
    <div>This page allows you to control your trading bot.</div>
    <br />
    <p>
      If you need any help, please refer to the
      <a href="https://www.phxstra.io/en/latest/">phxstra Documentation</a>.
    </p>

    <p>Have fun - <i>wishes you the phxstra team</i></p>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

import BotList from '@/components/BotList.vue';

@Component({
  components: { BotList },
})
export default class Home extends Vue {}
</script>

<style scoped>
.home {
  margin-top: 1.5em;
}
.logo-svg {
  -webkit-mask: url(../assets/phxstra-logo-mask.png) no-repeat center;
  mask: url(../assets/phxstra-logo-mask.png) no-repeat center;
  mask-size: contain;
  width: 250px;
  height: 250px;
}
</style>
