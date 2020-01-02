<template>
  <div class="setUIBox">
    <div class="popoutTitle setUITitle">
      <span>UI模板自动生成</span>
      <img src="../../BCCA-Demo/img/close.png" @click="close" />
    </div>
    <div>
      <iframe
        :src='"http://118.31.76.126:20001/device/UIEditor?productCode="+productcode'
        frameborder="0"
        @click="close"
      ></iframe>
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
    };
  },
  props: ["productcode"],
  methods: {
    close() {
      this.$emit("close");
    }
  }
};
</script>
 
<style>
.setUIBox {
  width: 90%;
  margin: 5% auto 0;
}
.setUITitle,
iframe .hello {
  background: rgba(27, 38, 51);
}
.setUIBox iframe {
  width: 100%;
  height: 100%;
}
.setUIBox > div:nth-child(2) {
  background: #e2e6ec;
  width: 100%;
  height: 600px;
}
</style>