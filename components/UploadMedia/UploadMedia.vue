<template>
	<view class="upload">
		<view class="list">
			<view class="item" v-for="item in files" :key="item.tempFilePath">
				<image v-if="item.fileType=='image'" :src="item.tempFilePath" style="width: 100%;height: 100%;" @click="preview(item.tempFilePath)"></image>
				<video v-else :src="item.tempFilePath" style="width: 100%;height: 100%;" controls @click="preview(item.tempFilePath)"></video>
				<view class="del" @click="deleteMedia(item)">
					<image src="../../static/close.svg" style="width: 50rpx;height: 50rpx;" mode=""></image>
				</view>
			</view>
			<view class="choose" @click="showAction">+</view>
		</view>
	</view>
</template>

<script setup lang="ts">
import {ref} from 'vue'
import {FileItem} from './model'

const files = ref<Array<FileItem>>([])

const showAction = () => {
	uni.chooseMedia({
		count: 9,
		mediaType: ['mix'],
		sourceType: ['album', 'camera'],
		maxDuration: 15,
		camera: 'back',
		success(res) {
		  files.value.push(...res.tempFiles)
		},
		fail(res){
			console.log(res);
		}
	})
}

const preview = (path:string) => {
	console.log(path);
}

const deleteMedia = (item:FileItem) => {
	uni.showModal({
		title: '确认操作',
		content: item.fileType=='image'?'是否要移除此照片':'是否要移除此视频',
		success: function (res) {
			if (res.confirm) {
				let index = files.value.findIndex(i => i.tempFilePath == item.tempFilePath)
				files.value.splice(index,1)
			} else if (res.cancel) {
				uni.showToast({
					title:'已取消删除',
					icon:'none'
				})
			}
		}
	});
}
</script>

<style scoped lang="less">
.upload{
	width: 90%;
	height: 50vh;
	margin: 300rpx auto;
	background-color: aquamarine;
	.list{
		width: 100%;
		display: grid;
		grid-template-rows:250rpx 250rpx 250rpx;
		grid-template-columns: 33% 33% 33%;
		gap: 0.5%;
		.item,.choose{
			box-sizing: border-box;
			border: 2rpx solid #494949;
			position: relative;
			.del{
				width: 50rpx;
				height: 50rpx;
				position: absolute;
				top: 10rpx;
				right: 10rpx;
				color: #A0A0A0;
			}
		}
		.choose{
			display: flex;
			justify-content: center;
			align-items: center;
			font-size: 100rpx;
		}
	}
}
</style>