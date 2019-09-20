<template>
  <div>
    <v-container>
      <v-tabs fixed-tabs slider-color="blue" >
        <v-tab @click.prevent="setTabCurrent(true)">今日天气</v-tab>
        <v-tab @click.prevent="setTabCurrent(false)">未来七天</v-tab>
      </v-tabs>
    </v-container>
  </div>
</template>

<script>
import store from "@/store.js";
export default {
  name: "DayForecastTab",
  data() {
    return {};
  },
  methods: {
    setTabCurrent: function(payload) {
      store.commit("setTabFlag", payload);
    }
  }
};
</script>


<style scoped lang="scss">
.displaytab {
  margin-top: 50px;
}
.tab{
  background-color: red !important;
}
</style>