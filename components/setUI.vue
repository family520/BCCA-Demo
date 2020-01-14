<template>
  <div class="setUIBox">
    <div class="popoutTitle setUITitle">
      <span>界面生成</span>
      <img src="../../BCCA-Demo/img/close.png" @click="close" />
    </div>
    <div class="UIBox">
      <img src="../../BCCA-Demo/img/zdsc.png" alt="">
      <br>
      <button class="zdscBtn">自动生成</button>
      <div class="popoutImgBox">
        <span class="imgShow">
          <img :src=imgSrc v-show="flag=='img'" />
          <div id="main" style="width:100%;height:3.4rem;" v-show="flag=='echart'"></div>
        </span>
      </div>
      <div class="popoutBtns">
        <input type="button" :value="btnValue" @click="close1" />
      </div>
    </div>

  </div>
</template>
 
<script>
module.exports = {
  mounted() {
    //首先看此设备是否能接入
    // console.log(this.choose_device.isSuccess);
    // let isSuccess =  this.choose_device.isSuccess;
    //
    // if(isSuccess){
    //   isSuccess = 100;
    //   this.imgSrc = "../../BCCA-Demo/img/success.png";
    // }
    // else{
    //   isSuccess = parseInt(Math.random() * 90)
    //   this.imgSrc = "../../BCCA-Demo/img/fail.png"
    // }

    // 基于准备好的dom，初始化echarts实例
    function echarsInit(myChart)
    {
      var data = [];
      var labelData = [];
      for (var i = 0; i < 100; ++i) {
        data.push({
          value: Math.random() * 10 + 10 - Math.abs(i - 12),
          name: i + ":00"
        });
        labelData.push({
          value: 1,
          name: i,
          itemStyle: {
            normal: {
              color: "#333"
            }
          }
        });
      }
      for (var i = 0; i < labelData.length; ++i) {
        if (labelData[i].name < 100) {
          labelData[i].itemStyle = {
            normal: {
              color: "#1477ca"
            }
          };
        }
      }
      // 指定图表的配置项和数据
      var option = {
        title: {
          text: isSuccess+"%",
          left: "50%",
          textAlign: "center",
          top: "45%",
          textStyle: {
            fontSize: 16,
            color: "#fff"
          }
        },
        series: [
          {
            hoverAnimation: false,
            type: "pie",
            data: labelData,
            radius: ["55%", "85%"],
            itemStyle: {
              normal: {
                borderWidth: 1,
                backgroundColor: "#000"
              }
            },
            label: {
              normal: {
                position: "inside",
                show: false
              }
            }
          }
        ]
      };
      // 使用刚指定的配置项和数据显示图表。
      myChart.setOption(option);
    }

    var myChart = echarts.init(document.getElementById("main"));
    echarsInit(myChart);
    setTimeout(() => {
      this.flag = "img";
      this.btnValue = "确定";
    }, 2000);



    // 浏览器窗口变化后需要做的事情
    //  重新绘制echarts
    window.onresize = function() {
      myChart.resize();
    };
  },
  data: function() {
    return {
      flag: "echart", //进入测试首先显示echart图
      imgSrc : "",
      btnValue : "取消",
    };
  },
  props: ["productcode"],
  methods: {
    close() {
      this.$emit("close");
    },
    changeActiveStyle(id){
        this.active = id;
    },
    close1() {
      if(this.btnValue == "确定"){
        this.$emit("close",'test',this.choose_device.isSuccess);
      }else {
        this.$emit("close");
      }
    }
  }
};
</script>
 
<style>
.setUIBox {
  width: 9.61rem;
  height: 7.66rem;
  margin: 0 auto;
  background: #1b2633;
  overflow: hidden;
}
.setUITitle,
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

.zdscBtn{
  position: absolute;
  top: 70%;
  left: 43.9%;
  width: 1.21rem;
  height: 0.37rem;
  line-height: 0.37rem;
  background: #00FFFF;
  font-family: MicrosoftYaHei;
  font-size: 0.16rem;
  color: #ffffff;
  border-radius: 0.04rem;
}

/* 模板内容盒子 */
.UIBox {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}
.UIBox img{
  width: 1.89rem;
  height: 2.01rem;
}
.popoutImgBox{
  position: absolute;
  top: 0;
  left: 0;
  border: 1px solid red;
  width: 7.01rem;
  height: 4.98rem;
  background-color: #131b2d;
  margin: auto;
  border-radius: 4px;
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 258px;
}

.popoutImgBox>.imgShow{
  display: inline-block;
  width: 100%;
  height: 2.75rem;
  text-align: center;
  margin-top: 0.6rem;

}

.popoutImgBox>.imgShow>img{
  height: 2.75rem;
}

.popoutBtns{
  margin-top: 0.69rem;
}
.popoutBtns>input{

  width: 1.21rem;
  height: 0.36rem;
  cursor: pointer;
  color: #ffffff;
  line-height: 0.36rem;
  text-align: center;
  border-radius: 3px;
  outline: none;
  margin: 0 0.2rem;

}

.popoutBtns>input:last-child{
  background: none;
  border: 1px solid #3C4148;
}

.popoutBtns>input:first-child{
  background-color: #0492F2;
  border: none;
}

</style>