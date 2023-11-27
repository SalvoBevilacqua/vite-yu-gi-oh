<script>
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";

export default {
  data() {
    return {
      list: []
    }
  },
  created() {
    axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0").then((resp) => {
      this.list = resp.data.data;
      return this.list;
    })
  }
}
</script>

<template>
  <h1 class="text-center">prova</h1>
  <!-- <AppHeader /> -->
</template>

<style lang="scss">
@use "./style/general.scss";
</style>
