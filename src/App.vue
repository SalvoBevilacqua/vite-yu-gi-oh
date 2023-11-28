<script>
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import { store } from "./store.js";

export default {
  components: {
    AppHeader,
    AppMain
  },
  data() {
    return {
      store
    }
  },
  created() {
    this.store.flagLoading = true;
    axios.get(this.store.apiUrl, {
      params: {
        num: 20,
        offset: 20
      }
    }).then((resp) => {
      this.store.cards = resp.data.data;
      this.store.flagLoading = false;
    })
  }
}
</script>

<template>
  <AppHeader />
  <AppMain />
</template>

<style lang="scss">
@use "./style/general.scss";
</style>
