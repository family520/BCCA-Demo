<template>
        <div class="popoutBox">

            <!-- 标题 -->
            
            <div class="popoutTitle">
                <span>执行计划</span>
                <img src="../../BCCA-Demo/img/close.png"
                    @click="close">
            </div>

            <!-- 内容 -->
            <div class="popoutImgBox">

                <div class="formBox addPlan">
                    
                    <p>添加执行计划</p>

                    <div class="addPlanBox">

                        <div class="formItem addPlanItems">

                            <label for="" class="addPlanItem">
                                <span class="textHiden">执行计划:</span>
                                <input type="text">
                            </label>

                            <label for="" class="addPlanItem">
                                 <span class="textHiden">前置动作:</span>
                                 <input type="text">
                            </label>

                             <label for="" class="addPlanItem">
                                <span class="textHiden">前置时间(秒s):</span>
                                <input type="text">
                            </label>

                             <label for="" class="addPlanItem">
                                 <span class="textHiden"> 延时时间(秒s):</span>
                                <input type="text">
                            </label>


                        </div>


                    </div>

                </div>

                <!-- 绑定模式 -->
                <div class="formBox bindModel">

                     <p>绑定模式（建议单选）</p>

                    <div class="bindModelBox">

                        <div class="formItem bindModelItems">

                            <label :for="item.name" 
                            class="bindModelItem" 
                            v-for="(item,i) in modelList" :key="item.id">
                                <input type="checkbox" :id="item.name">
                                <span class="textHiden">{{item.name}}</span>
                            </label>

                        </div>


                    </div>

                </div>

                <div class="popoutBtns bindModelBtns">
                    

                    <input type="button"  @click="close" value="保存">
                    <input type="button"  @click="close" value="取消">

                </div>


            </div>


        </div>
</template>
 
<script>
module.exports = {
    data: function() {
        return {
            modelList:[
                {id:1,name:"会客模式"},
                {id:2,name:"离家模式"},
                {id:3,name:"回家模式"},
                {id:5,name:"观影模式"},
                {id:6,name:"夜间模式"},
                {id:7,name:"白昼模式"},
                {id:8,name:"K歌模式"},
                {id:9,name:"浪漫晚餐模式"},
                {id:10,name:"睡眠模式"},
                {id:11,name:"起床模式"},
                {id:12,name:"早餐模式"},
                {id:13,name:"安防模式"},
                {id:14,name:"守护模式"},
                {id:15,name:"阅读模式"},
                {id:16,name:"聚会模式"},
                {id:17,name:"娱乐模式"},
                {id:18,name:"运动模式"},
                {id:19,name:"办公模式"},
        
            ]
        }
    },
    methods: {
        close(){
            this.$emit('close');
        }
    },
}
</script>
 
<style>
</style>