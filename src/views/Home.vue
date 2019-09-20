<template>
  <div class="home">
    <!-- <img class="homepageLogo" src ="https://www.iosicongallery.com/icons/weather-2017-06-19/512.png"/> -->
    <SearchBar />
    <Select />
    <v-card max-width="1500" class="mx-auto margin">
      <v-card-title class="flexTab">
        <DayForecastTab />
      </v-card-title>
      <v-card-text>
        <Weather />
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
import Weather from "@/components/Weather.vue";
import SearchBar from "@/components/SearchBar.vue";
import DayForecastTab from "@/components/DayForecastTab.vue";
import Select from "@/components/Select.vue";

export default {
  name: "home",
  components: {
    Weather,
    SearchBar,
    DayForecastTab,
    Select
  },
  mounted() {},
  methods: {}
};
</script>
<style scoped lang="scss">
.flexTab{
  display: flex;
  justify-content: center;
  align-items: center;
}
.margin{
  margin-top: 40px;
}
</style>

