<template>
  <div v-if="weatherCache!=null">
    <v-container class="areaInfo">
          <h4>市：{{weatherCache.location.name}}</h4>
          <h4>省：{{weatherCache.location.region}}</h4>
          <h4>国家：{{weatherCache.location.country}}</h4>
    </v-container>

    <v-container class="currentCondition animation" v-if="isTabFlagCurrent">
      <img v-bind:src="weatherCache.current.condition.icon" />
      <h3>{{weatherCache.current.feelslike_c}}°c</h3>
      <h3>{{weatherCache.current.condition.text}}</h3>
    </v-container>

    <v-container v-if="!isTabFlagCurrent">
      <b-row name>
        <b-col v-for="day in weatherCache.forecast.forecastday" :key="day.id" class="animation">
          <img v-bind:src="day.day.condition.icon" />
          <p>平均温度: {{day.day.avgtemp_c}}°c</p>
          <p>{{day.day.condition.text}}</p>
          <p>{{day.date}}</p>
        </b-col>
      </b-row>
    </v-container>
  </div>
</template>

<script>
import store from "@/store.js";
export default {
  name: "Weather",
  data() {
    return {
      weatherForecast: null
    };
  },
  mounted() {
    store.commit("setTabFlag", true);
    store.dispatch("searchLocation", "chongqing");
  },
  computed: {
    weatherCache: () => store.getters["getWeatherCache"],
    isTabFlagCurrent: () => store.getters["getTabFlag"]
  }
};
</script>

<style scoped lang="scss">
.currentWeatherIcon {
  width: 10%;
  height: 10%;
}
.animation{
  animation-duration: 2s;
  animation-name: out;
}

@keyframes out {
  from{
    opacity: 0;
  }
  to{
    opacity: 1;
  }
}
</style>
