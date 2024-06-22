<template>
	<view class="avatarAndName">
		<view class="avatarBtn">
			<button class="btn" open-type="chooseAvatar" @chooseavatar="onChooseAvatar">
				<image style="width: 160rpx;height: 160rpx;" :src="avatarUrlValue"></image>
			</button>
		</view>
		<view class="tip"><text>点击设置头像</text></view>
		<view class="name">
			<text>昵称</text>
			<input class="nicknamestyle" @change="inputBlur" v-model="nickName" type="nickname" placeholder="请输入昵称" name="nickname" />
		</view>
		<view class="btn">
			<wd-button type="success" @click="handleFinish">完成</wd-button>
		</view>
		
		
	</view>
</template>

<script setup lang="ts">
import {ref} from 'vue'
	
const nickName = ref<string>('')
const avatarUrlValue = ref<string>('../../static/noAvatar.png')
const onChooseAvatar = (e) => {
	avatarUrlValue.value = e.detail.avatarUrl
}

const inputBlur = (e) => {
	nickName.value = e.detail.value
}

const handleFinish = () => {
	uni.switchTab({
		url:'/pages/index/index'
	})
}
</script>

<style scoped lang="less">
.avatarAndName{
	padding-top: 200rpx;
	.avatarBtn{
		width:160rpx;
		height: 160rpx;
		margin: 0 auto;
		padding: 0;
		button{
			padding: 0;
			display: flex;
			justify-content: center;
			align-items: center;
		}
	}
	.tip{
		height: 50rpx;
		line-height: 50rpx;
		font-size: 24rpx;
		text-align: center;
	}
	.name{
		display: flex;
		align-items: center;
		height: 100rpx;
		margin: 40rpx 0;
		background-color: #fff;
		text{
			display: block;
			width: 150rpx;
			text-align: center;
		}
	}
	.btn{
		display: flex;
		align-items: center;
		justify-content: center;
	}
}
</style>
