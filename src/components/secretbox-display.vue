<template>
    <div>
        <div class="ui large top attached tabular menu">
            <a :class="[ 'item', { 'active': tab.secret_box_tab_id === tab_display_id } ]" v-for="tab in tabList" :key="tab.secret_box_tab_id" @click="tab_display_id = tab.secret_box_tab_id">
                <img class="ui image" :src="`//rawfile.skufes.moe/${tab.title_img_asset}`">
            </a>
            <div class="right menu">
                <div class="header item">{{name}}</div>
            </div>
        </div>
        <div class="ui bottom attached segment cards container">
            <secretbox-card v-for="page in currTab.page_list" :key="page.secret_box_page_id" :page="page"></secretbox-card>
        </div>
    </div>
</template>
<script>
import Vue from 'vue'
import SecretboxCard from './secretbox-card.vue'
import _ from 'lodash'
Vue.component('secretbox-card', SecretboxCard)
export default {
    props: [ 'tabList', 'name' ],
    data: function () {
        return {
            tab_display_id: 1
        }
    },
    computed: {
        currTab: function() {
            return _.find(this.tabList, tab => tab.secret_box_tab_id === this.tab_display_id)
        }
    },
    methods: {
    }
}
</script>
<style>
.ui.header>img.secretbox-header {
    height: auto;
    width: auto;
}
</style>
