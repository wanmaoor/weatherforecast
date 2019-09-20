<template>
  <v-region @values="regionChange" :area="false" class="select"></v-region>
</template>

<script>
import { map } from "../assets/map.js";
import store from "@/store.js";
export default {
  name: 'Select',
  methods: {
    regionChange(data) {
      let cityName = data.city.value;
      let provinceName = data.province.value;

      function convertRegion(cityName, provinceName) {
        cityName = map.get(cityName);
        provinceName = map.get(provinceName);
        return { cityName, provinceName };
      }
      let res = convertRegion(cityName, provinceName);
      console.log("res:", res);
      let city = "";
      let province = "";
      if (data.city.value && data.province.value) {
        console.log("市:", data.city.value);
        console.log("省:", data.province.value);
        store.dispatch(
          "searchLocation",
          `${res.cityName}, ${res.provinceName}`
        );
      }
    }
  }
}
</script>

<style>
  .select{
    margin-bottom: 50px;
  }
</style>