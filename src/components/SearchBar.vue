<template>
  <div>
    <v-container>
      <v-layout>
        <v-region @values="regionChange" :area="false"></v-region>
        <v-flex xs12 sm12 md12 lg6 offset-lg3 offset-md1>
          <v-text-field
            solo
            label="搜索地点"
            v-model="searchValue"
            @keyup.enter.native="searchLocation(searchValue)"
            append-icon="search"
            @click:append="searchLocation(searchValue)"
          ></v-text-field>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
import store from "@/store.js";
import service from "@/service.js";
import {map} from '../assets/map.js';
export default {
  name: "SearchBar",
  data() {
    return {
      searchValue: null
    };
  },
  methods: {
    searchLocation(payload) {
      store.dispatch("searchLocation", payload);
    },
    regionChange(data) {
      let cityName = data.city.value
      let provinceName = data.province.value
     
      function convertRegion(cityName, provinceName){
        cityName = map.get(cityName)
        provinceName = map.get(provinceName)
        return {cityName, provinceName}
      }
      let res = convertRegion(cityName, provinceName)
      console.log('res:',res);
      let city = ''
      let province = ''
      if(data.city.value && data.province.value){
        console.log('市:',data.city.value);
        console.log('省:',data.province.value);
        store.dispatch("searchLocation", `${res.cityName}, ${res.provinceName}`)
      }
    }
    
  }
};
</script>

<style scoped lang="scss">
.searchbar {
  width: 50%;
}
</style>