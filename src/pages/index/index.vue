<template>
  <div class="index">
    <div class="swiper">
      <swiper class="swiper-container" indicator-dots="true" autoplay="true" interval="3000" circular="true" duration="500">
        <block v-for="(item, index) in banner " :key="index">
          <swiper-item class="swiper-item">
            <image :src="item.image_url" class="slide-image" />
          </swiper-item>
        </block>
      </swiper>
    </div>
    <div class="channel">
      <div v-for="(item, index) in channel" :key="index">
        <img :src="item.icon_url" alt="">
        <p>{{item.name}}</p>
      </div>
    </div>
  </div>
</template>

<script>
import { get } from "../../utils";
export default {
  data() {
    return {
      banner: [],
      channel: []
    };
  },
  components: {},
  methods: {
    async getData() {
      var data = await get("/index/index");
      this.banner = data.banner;
      this.channel = data.channel;
    }
  },
  created() {
    // 调用应用实例的方法获取全局数据
    this.getData();
  }
};
</script>

<style lang='scss' scoped>
@import "./style.scss";
</style>
