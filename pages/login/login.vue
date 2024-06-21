<template>
	<view class="login">
		<view class="space"></view>
		<view class="logo">LOGO</view>
		<view class="action">
			<button @click="handleLogin" style="background-color: #31AE37;color: #fff;">微信快捷登录</button>
			<view class="tips">
				<radio :checked="check" activeBackgroundColor="#31AE37" style="transform: scale(0.6);" @click="handleCheck"></radio>
				<text>点击即代表同意<text style="color: #1c80f9;">《用户协议》</text>及<text style="color: #1c80f9;">《隐私政策》</text></text>
			</view>
		</view>
	</view>
</template>

<script setup lang="ts">
import {ref} from 'vue'
import {createToast} from '../../utils/feedback'

const check = ref<boolean>(false)

const handleCheck = () => {
	check.value = !check.value
}

const handleLogin = () => {
	if(check.value){
		uni.switchTab({
			url:'/pages/index/index'
		})
	}else{
		createToast("请先查看并同意用户协议及隐私政策")
	}
}

</script>

<style lang="less" scoped>
.login{
	width: 100vw;
	height: 100vh;
	background: url(../../static/back.png) no-repeat;
	background-size: cover;
	.space{
		height: 400rpx;
	}
	.logo{
		width: 100%;
		height: 200rpx;
		display: flex;
		justify-content: center;
		align-items: center;
	
		//替换
		font-size: 48rpx;
		font-weight: bold;
	}
	.action{
		margin: 300rpx 24rpx 0;
		.tips{
			display: flex;
			align-items: center;
			margin-top: 10rpx;
			color: #636363;
		}
	}
}
</style>
