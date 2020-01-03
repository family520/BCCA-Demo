<template>
    <div class="popoutBox popoutUploadBox">
        <!-- 标题 -->

        <div class="popoutTitle">
            <span>上传指令文件</span>
            <img
                    src="../../BCCA-Demo/img/close.png"
                    @click="close"/>
        </div>

        <!-- 内容 -->
        <div class="UploadBox">
            <input type="file">
            <button @click="close1">提交</button>
        </div>
    </div>
</template>

<script>
    module.exports = {
        data: function () {
            return {};
        },
        methods: {

            close() {
                this.$emit('close');
            },
            close1() {
                this.$emit('close', 'upload');
            }
        },
    };
</script>

<style>
</style>