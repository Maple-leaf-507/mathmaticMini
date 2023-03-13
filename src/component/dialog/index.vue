<template>
    <view class="mock"  v-if="show" @click="closeDialog">
        <view class="content">
            <slot>
                该功能暂未开放......
            </slot>
        </view>
    </view>
</template>

<script setup lang="ts">
import { defineEmits } from 'vue'
let props = defineProps<{
    show:boolean
}>()

let emits = defineEmits(['sendShow'])

// 关闭弹框
const closeDialog = () => {
    console.log('关闭弹框')
    emits('sendShow',!props.show)
}
</script>

<style scoped>
    .mock{
        z-index: 999999;
        position: absolute;
        top: 0;
        width: 750rpx;
        box-sizing: border-box;
        height: 100vh;
        background: rgba(0,0,0,.2);
    }
    .content{
        border:1px solid rgb(189, 189, 189);
        border-radius: 10px;
        background: #ebf7f9;
        width: 300rpx;
        height: 200rpx;
        margin-top: 517rpx;
        margin-left: 275rpx;
        text-align: center;
        line-height: 200rpx;
        font-size: 30rpx;
    }
</style>
