<template>
  <div class="popoutBox">
    <!-- 标题 -->

    <div class="popoutTitle">
      <span>执行计划</span>
      <img src="../../BCCA-Demo/img/close.png" @click="close" />
    </div>

    <!-- 内容 -->
    <div class="popoutImgBox">
      <div class="formBox addPlan">
        <p>添加执行计划</p>

        <div class="addPlanBox">
          <div class="formItem addPlanItems">
            <label for class="addPlanItem">
              <span class="textHiden">执行计划:</span>
              <input type="text" v-model="executePlan" />
            </label>

            <label for class="addPlanItem">
              <span class="textHiden">前置动作:</span>
              <select v-model="prepositionActive">
                <option value="1" class="textHiden">前置动作1</option>
                <option value="2" class="textHiden">前置动作2</option>
                <option value="3" class="textHiden">前置动作3</option>
              </select>
            </label>

            <label for class="addPlanItem">
              <span class="textHiden">前置时间(秒s):</span>
              <input type="text" v-model="prepositionTime" />
            </label>

            <label for class="addPlanItem">
              <span class="textHiden">延时时间(秒s):</span>
              <input type="text" v-model="delayTime" />
            </label>
          </div>
        </div>
      </div>

      <!-- 绑定模式 -->
      <div class="formBox bindModel">
        <p>绑定模式（建议单选）</p>

        <div class="bindModelBox">
          <div class="formItem bindModelItems">
            <label
              :for="item.name"
              class="bindModelItem"
              v-for="(item,i) in modelList"
              :key="item.id"
            >
              <input
                type="checkbox"
                :checked="item.isCheck"
                :id="item.name"
                @click="addBindModelList(i)"
              />
              <span class="textHiden">{{item.name}}</span>
            </label>
          </div>
        </div>
      </div>

      <div class="popoutBtns bindModelBtns">
        <input type="button" @click="close" value="保存" />
        <input type="button" @click="reset" value="重置" />
      </div>
    </div>
  </div>
</template>
 
<script>
module.exports = {
  data: function() {
    return {
      executePlan: "", //执行计划
      prepositionActive: "1", //前置动作
      prepositionTime: "", //前置时间
      delayTime: "", //延时时间
      modelList: [
        { id: 1, isCheck: false, name: "会客模式" },
        { id: 2, isCheck: false, name: "离家模式" },
        { id: 3, isCheck: false, name: "回家模式" },
        { id: 4, isCheck: false, name: "观影模式" },
        { id: 5, isCheck: false, name: "夜间模式" },
        { id: 6, isCheck: false, name: "白昼模式" },
        { id: 7, isCheck: false, name: "K歌模式" },
        { id: 8, isCheck: false, name: "浪漫晚餐模式" },
        { id: 9, isCheck: false, name: "睡眠模式" },
        { id: 10, isCheck: false, name: "起床模式" },
        { id: 11, isCheck: false, name: "早餐模式" },
        { id: 12, isCheck: false, name: "安防模式" },
        { id: 13, isCheck: false, name: "守护模式" },
        { id: 14, isCheck: false, name: "阅读模式" },
        { id: 15, isCheck: false, name: "聚会模式" },
        { id: 16, isCheck: false, name: "娱乐模式" },
        { id: 17, isCheck: false, name: "运动模式" },
        { id: 18, isCheck: false, name: "办公模式" }
      ]
    };
  },
  methods: {
    close() {
      this.$emit("close");
    },
    addBindModelList(index) {
      this.modelList[index].isCheck = !this.modelList[index].isCheck;
    },
    reset() {
      //重置
      for (let i = 0; i < this.modelList.length; i++) {
        this.modelList[i].isCheck = false;
      }
      this.executePlan = this.prepositionTime = this.delayTime = "";
      this.prepositionActive = "1";
    }
  }
};
</script>
 
<style>
</style>