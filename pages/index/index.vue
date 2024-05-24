<template>
	<view class="index">
		<wd-fab type="success" position="right-bottom" direction="top" :draggable="true">
			<view class="item">活动</view>
			<view class="item" style="margin-bottom:10rpx;">打卡</view>
		</wd-fab>
		<view class="test">
			<button @click="testToast">测试轻提示</button>
		</view>
	</view>
</template>


<script setup lang="ts">
import {createActionSheet} from '../../utils/uni_utils'
const testToast = () => {
	createActionSheet(['1','2','3','2','3','2','3'],(res) => {
		console.log(res.tapIndex);
		
	})
}
</script>

<style lang="less" scoped>
.index {
	width: 100%;
	height: 100vh;
	
}
.item{
	width: 70rpx;
	height: 70rpx;
	border-radius:50%;
	background-color: #31AE37;
	display:flex;
	align-items: center;
	justify-content: center;
	font-size: 24rpx;
	color:#E0E0E0;
}
</style>
