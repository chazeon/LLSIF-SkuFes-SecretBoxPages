<template>
    <div class="ui card">
        <div class="image">
            <img :src="`//rawfile.skufes.moe/${page.default_img_info.img_asset}`">
            <img src="//rawfile.skufes.moe/assets/image/ui/secretbox/se_etc_10.png" class="after">
        </div>
        <div class="content">
            <a class="header">{{page.secret_box_list[page.secret_box_list.length - 1].name}}</a>
            <div class="meta">
                <span class="date" v-if="page.limited_img_info[0]">{{page.limited_img_info[0].end_date}}</span>
            </div>
            <!--div class="description">
            {{page.secret_box_list[0].description}}
            </div-->

        </div>
        <a class="ui bottom attached button" :href="`//news.skufes.moe/${page.default_img_info.url}`">
                Detail
        </a>
    </div>
</template>
<script>
export default {
    props: [ 'page' ]
}
</script>
<style>
img.after {
    position: absolute;
    bottom: 0px;
}
</style>
