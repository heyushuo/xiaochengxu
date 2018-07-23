<template>
  <div class="index">
    <div class="swiper">
      <swiper indicator-dots="true" autoplay="true" interval="3000" circular="true" duration="500">
        <block v-for="(item, index) in imgUrls" :key="index">
          <swiper-item>
            <image :src="item" class="slide-image" width="100%" height="150" />
          </swiper-item>
        </block>
      </swiper>
    </div>
  </div>
</template>

<script>
import { get } from "../../utils";
export default {
  data() {
    return {
      imgUrls: [
        "http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg",
        "http://img06.tooopen.com/images/20160818/tooopen_sy_175866434296.jpg",
        "http://img06.tooopen.com/images/20160818/tooopen_sy_175833047715.jpg"
      ]
    };
  },
  components: {},
  methods: {
    async getData() {
      var data = await get("http://192.168.2.1:9996/app/index/index");
      console.log(data);
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
