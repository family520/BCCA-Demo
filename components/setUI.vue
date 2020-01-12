<template>
  <!-- <iframe
        :src='"http://118.31.76.126:20001/device/UIEditor?productCode="+productcode'
        frameborder="0"
        @click="close"
  ></iframe>-->

  <!-- 备用 -->
  <div class="setUIBox">
    <div class="popoutTitle setUITitle">
      <span>UI模板自动生成</span>
      <img src="../../BCCA-Demo/img/close.png" @click="close" />
    </div>
    <div class="UIBox">
      <div 
      v-for="(item,key,i) in uIList" 
      :key = "i"
      :class="{'activeStyle': active==item.id}" 
      @click="changeActiveStyle(item.id)">
        <img :src="item.src" alt />
      </div>
    </div>
    <div class="popoutBtns setUIBtns">
      <!--        <input type="button" value="接入" @click="close1" v-show="choose_device.isSuccess && flag == 'img'" />-->
      <input type="button" value="确定" @click="close" />
      <input type="button" value="重置" @click="active=''" />
    </div>
  </div>
</template>
 
<script>
module.exports = {
  mounted() {
    //   console.log('productcode:', this.productcode)
  },
  data: function() {
    return {
      uIList: [
        { id: 1, src: "../../BCCA-Demo/img/fail.png" },
        { id: 2, src: "../../BCCA-Demo/img/fail.png" },
        { id: 3, src: "../../BCCA-Demo/img/fail.png" }
      ],
      active : "", //被点击选中的UI模板
    };
  },
  props: ["productcode"],
  methods: {
    close() {
      this.$emit("close");
    },
    changeActiveStyle(id){
        this.active = id;
    }
  }
};
</script>
 
<style>
.setUIBox {
  width: 90%;
  margin: 0 auto;
  background: #1b2633;
}
.setUITitle,
iframe .hello {
  background: rgb(27, 38, 51);
}
.setUIBox iframe {
  width: 100%;
  height: 100%;
}
.setUIBox > div:nth-child(2) {
  background: #131b2d;
  width: 96%;
  height: calc(100vh - 2.6rem);
  margin: 0 2%;
}
.setUIBtns {
  margin-top: 0;
  background: #e2e6ec;
  text-align: center;
  padding: 0.2rem 0;
  background: #1b2633;
}

/* 模板内容盒子 */
.UIBox {
  display: flex;
  justify-content: space-around;
  align-items: center;
}
.UIBox > div {
  cursor: pointer;
  border: 1px solid #1b2633;
  padding: 0.3rem;
}
.UIBox .activeStyle{
  border : 3px solid #0492F2
}
</style>