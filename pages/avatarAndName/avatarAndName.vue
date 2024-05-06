<template>
	<view class="avatarAndName">
		<view class="avatarBtn">
			<button class="btn" open-type="chooseAvatar" @chooseavatar="onChooseAvatar">
				<image style="width: 160rpx;height: 160rpx;" :src="avatarUrlValue"></image>
			</button>
		</view>
		<view class="name">
			<text>昵称</text>
			<input class="nicknamestyle" @change="inputBlur" v-model="nickName" type="nickname" placeholder="请输入昵称" name="nickname" />
		</view>
		
		
	</view>
</template>

<script setup lang="ts">
import {ref} from 'vue'
	
const nickName = ref<string>('')
const avatarUrlValue = ref<string>('../../static/noAvatar.png')
const onChooseAvatar = (e) => {
	console.log(e);
}

const inputBlur = (e) => {
	console.log(e);
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
	.name{
		display: flex;
		align-items: center;
		height: 100rpx;
		margin-top: 40rpx;
		border-top: 2rpx solid #999;
		border-bottom: 2rpx solid #999;
		text{
			display: block;
			width: 150rpx;
			text-align: center;
		}
	}
	
}
</style>
