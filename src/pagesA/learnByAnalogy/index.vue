<template>
    <view style="position:fixed;top:0;left:0">
        <image src="@/static/indexBg.jpg" class="bg"></image>
        <view class="content">
            <view v-for="item in stage">
                <CheckBox />{{ item.name }}
            </view>
        </view>
    </view>
   
</template>

<script setup lang="ts">
import CheckBox from '@/component/checkBox/index.vue'

import { ref } from 'vue'

const stage = ref([
    {
        name: '0~10',
        id:0
    },
    {
        name: '0~20',
        id:1
    }
])
</script>

<style scoped>
    .bg{
		width: 100vw;
		height: 100vh;
	}
    .content{
		margin-top:20rpx;
		position: absolute;
		top:0;
	}
</style>
