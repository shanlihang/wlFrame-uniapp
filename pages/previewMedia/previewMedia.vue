<template>
	<view class="preview">
		<view class="media">
			<swiper class="swiper" circular :current="data.current" @change="changeHandle">
				<swiper-item class="item" v-for="(item,index) in data.list" :key="item.tempFilePath" :item-id="index">
					<view class="swiper-item">
						<image v-if="item.fileType=='image'" :src="item.tempFilePath" mode="aspectFit"></image>
						<video v-else :src="item.tempFilePath" controls></video>
					</view>
				</swiper-item>
			</swiper>
		</view>
		<view class="current">{{data.current+1}}/{{data.list.length}}</view>
		<view class="close" @click="returnPre">
			<image src="../../static/close.svg" style="width: 50rpx;height: 50rpx;" mode=""></image>
		</view>
	</view>
</template>

<script setup lang="ts">
import {onLoad} from '@dcloudio/uni-app'
import {reactive} from 'vue'

const data = reactive({
	list:[],
	current:0
})

const returnPre = () => {
	uni.navigateBack()
}

const changeHandle = (e) => {
	console.log(e.detail.currentItemId);
	data.current = parseInt(e.detail.currentItemId);
}

onLoad((option) => {
	data.current = parseInt(option.current)
	data.list = JSON.parse(option.list)
})

</script>

<style scoped lang="less">
.preview{
	width: 100vw;
	height: 100vh;
	position: relative;
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	background-color: rgba(0, 0, 0, .8);
	.media{
		width: 100vw;
		height: 70vh;
		.swiper{
			width: 100%;
			height: 100%;
			display: flex;
			justify-content: center;
			align-items: center;
			.item{
				display: flex;
				justify-content: center;
				align-items: center;
			}
		}
	}
	.current{
		margin-top: 50rpx;
		color: #E0E0E0;
	}
	.close{
		position: absolute;
		top: 50rpx;
		right: 50rpx;
	}
}
</style>
