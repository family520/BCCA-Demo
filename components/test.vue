<template>
  <div class="popoutBox">
    <!-- 标题 -->

    <div class="popoutTitle">
      <span>测试</span>
      <img src="../../BCCA-Demo/img/close.png" @click="close" />
    </div>

    <!-- 内容 -->
    <div class="popoutImgBox">
      <span class="imgShow">
        <img :src=imgSrc v-show="flag=='img'" />

        <div id="main" style="width:100%;height:3.4rem;" v-show="flag=='echart'"></div>
      </span>

      <div class="popoutBtns">
<!--        <input type="button" value="接入" @click="close1" v-show="choose_device.isSuccess && flag == 'img'" />-->
        <input type="button" :value="btnValue" @click="close1" />
      </div>
    </div>
  </div>
</template>
 
<script>
module.exports = {
  mounted() {

    //首先看此设备是否能接入
    //  console.log('checkedItem:', this.choose_device)

    let isSuccess =  this.choose_device.isSuccess;

    if(isSuccess){
        isSuccess = 100;
        this.imgSrc = "../../BCCA-Demo/img/success.png";
    }
    else{
        isSuccess = parseInt(Math.random() * 90)
        this.imgSrc = "../../BCCA-Demo/img/fail.png"
    }

    // 基于准备好的dom，初始化echarts实例
    function echarsInit(myChart,isSuccess) 
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
        if (labelData[i].name < isSuccess) {
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
    echarsInit(myChart,isSuccess);
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

   props: ['choose_device'],
  data: function() {
    return {
      flag: "echart", //进入测试首先显示echart图
      imgSrc : "",
      btnValue : "取消",
    };
  },
  
  methods: {
    close() {
      this.$emit("close");
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
</style>