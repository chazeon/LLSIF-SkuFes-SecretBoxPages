<template>
  <div class="ui container">
      <div class="ui vertical segment" v-if="gauge_info">
          <secretbox-display :tab-list="gauge_info[0].tab_list" name="μ's"></secretbox-display>
      </div>
      <div class="ui vertical segment" v-if="gauge_info">
          <secretbox-display :tab-list="gauge_info[1].tab_list" name="Aqours"></secretbox-display>
      </div>
  </div>
</template>
<script>
import Vue from 'vue'
import VueResource from 'vue-resource'
Vue.use(VueResource)
import SecretBoxDisplay from './components/secretbox-display.vue'
Vue.component('secretbox-display', SecretBoxDisplay)
import _ from 'lodash'
export default {
    data: function () {
        return {
            gauge_info: null
        }
    },
    created: function () {
        this.$http.get('//api.skufes.moe/gauge_info/')
        .then(response => {
            this.gauge_info = response.body
        })
    }
}
</script>
