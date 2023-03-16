<template>
	<view style="position:fixed;top:0;left:0">
		<image src="@/static/indexBg.jpg" class="bg"></image>
		<view class="content">
			<!-- <view class="stage">学段：</view> -->
			<!-- <view class="class">
				<view class="category_1">
					<view class="learn" @click="learn">学习乐园</view>
					<view class="simulation" @click="simulationClick">举一反三</view>
				</view>
				<view class="category_2">
					<view class="calculation" @click="calculationClick">计算模拟</view>
					<view class="learnNote" @click="learnNote">学习笔记</view>
				</view>
				<view class="category_2">
					<view class="errorSet" @click="errorSet">错题集合</view>
					<view class="photoSearch" @click="photoSearch">更多功能</view>
				</view>
			</view> -->
			<view class="title">请选择试题范围:</view>
			<uni-data-checkbox v-model="checkBox" :localdata="range" @change="changeCheckbox"></uni-data-checkbox>
			<view class="start" v-if="!flag" @click="startBut">开始</view>
			<view class="countdown" v-if="flag">{{countdown}}</view>
		</view>
	</view>
	<!-- <Dialog :show="show" @sendShow="sendShow"></Dialog> -->
</template>

<script setup lang="ts">
// import Dialog from '@/component/dialog/index.vue'
import { ref } from 'vue'

// const show = ref<boolean>(false)
const flag = ref<boolean>(false)

let countdown = ref<number>(3)

// checkbox
const checkBox = ref<number>(10)
const range = ref<Array<object>>([{"value": 10,"text": "0-10"	},{"value": 20,"text": "0-20"},{"value": 100,"text": "0-100"}])

// const mathData = ref<Array<object>>([])

// 选择弹框
const changeCheckbox =(e:any) => {
	console.log('11111111111',e.detail.value)
	// mathData.value
	const num1 = Math.floor(Math.random()*e.detail.value)
	console.log('打印随机数',num1)
}

const startBut = () => {
	console.log('点击开始按钮')
	flag.value = true
	let timer = setInterval(()=>{
		if(countdown.value===0){
			flag.value = false
			countdown.value = 3
			clearInterval(timer)
			return
		}
		countdown.value = countdown.value -1
	},1000)
}

// // 学习天地
// const learn = () => {
// 	show.value = true
// 	console.log('学习乐园')
// }

// // 举一反三
// const simulationClick = () => {
// 	uni.navigateTo({url: '/pagesA/learnByAnalogy/index'})
// }

// // 计算模拟
// const calculationClick = () => {
// 	show.value = true
// 	console.log('计算器============')
// }

// // 拍照搜题
// const photoSearch = () => {
// 	show.value = true
// 	console.log('拍照搜题')
// }

// // 错题集合
// const errorSet = () => {
// 	show.value = true
// 	console.log('错题集合')
// }

// // 学习笔记
// const learnNote = () => {
// 	show.value = true
// 	console.log('学习笔记')
// }

// // 隐藏弹框
// const sendShow = () => {
// 	show.value = false
// }


</script>

<style lang="scss">
@import "./index.scss";
	.bg{
		width: 100vw;
		height: 100vh;
	}
	.content{
		margin-top:20rpx;
		position: absolute;
		top:0;
	}
	.stage{
		padding-left: 50rpx;
	}
	.class{
		width: 750rpx;
		box-sizing: border-box;
		margin-top:100rpx;
		color:#393838;
		font-size: 32rpx;
	}
	.category_1, .category_2{
		display: flex;
		justify-content: space-around;
	}
	.category_2{
		margin-top:100rpx;
	}
	.learn, .simulation, .calculation, .learnNote, .photoSearch, .errorSet{
		width: 200rpx;
		height: 200rpx;
		border: 1px solid rgb(216, 216, 216);
		text-align: center;
		line-height: 200rpx;
	}
</style>
