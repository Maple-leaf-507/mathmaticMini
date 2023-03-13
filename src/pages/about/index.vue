<template>
  <view style="position:fixed;top:0;left:0">
    <image src="@/static/indexBg.jpg" class="bg"></image>
    <view class="content">
      <view class="cell_1" @click="contactCustomer">
        <view class="cell-left">
          <image src="@/static/customer-service.png" class="icon_1"></image>
          <view class="contactCustomer" >联系客服</view>
        </view>
        <image src="@/static/arroe-right.png" class="icon_1"></image>
      </view>
      <view class="cell_2"  @click="functionalFeedback">
        <view class="cell-left">
          <image src="@/static/function-feedback.png" class="icon_2"></image>
          <view class="functionalFeedback">功能反馈</view>
        </view>
        <image src="@/static/arroe-right.png" class="icon_2"></image>
      </view>
    </view>
  </view>
  <Dialog :show="show" @sendShow="sendShow"></Dialog>
</template>
  
<script setup lang="ts">
import Dialog from '@/component/dialog/index.vue'
import { ref } from 'vue'

const show = ref<boolean>(false)


// 联系客服
const contactCustomer = () => {
  // show.value = true
  uni.makePhoneCall({
    phoneNumber: '18744776542' //仅为示例
  });
  console.log('联系客服')
}

// 功能反馈
const functionalFeedback = () => {
  show.value = true
  console.log('功能反馈')
}

// 隐藏弹框
const sendShow = () => {
	show.value = false
}

</script>
  
<style scoped>
  .bg{
		width: 100vw;
		height: 100vh;
	}
  .content{
    width: 750rpx;
    box-sizing: border-box;
		margin-top:20rpx;
		position: absolute;
		top:0;
    font-size: 40rpx;
    padding: 10rpx;
	}
  .cell_1, .cell_2{
    padding: 10rpx;
    border-radius: 10rpx;
    justify-content: space-between;
    display: flex;
    border:1rpx solid rgb(226, 226, 226);
    height: 100rpx;
    line-height: 100rpx;
  }
  .cell-left{
    display: flex;
  }
  .icon_1, .icon_2{
    margin: auto 0 20rpx;
    width:50rpx;
    height:50rpx;
    margin-right: 20rpx;
  }
  .cell_2{
    margin-top:30rpx;
  }
</style>
  