<template>
	<view class="upload">
		<view class="list">
			<view class="item" v-for="item in files" :key="item.tempFilePath">
				<image v-if="item.fileType=='image'" :src="item.tempFilePath" style="width: 98%;height: 98%;" @click="preview(item.tempFilePath)"></image>
				<video v-else :src="item.tempFilePath" style="width: 98%;height: 98%;" controls @click="preview(item.tempFilePath)"></video>
				<view class="del" @click="deleteMedia(item)" v-if="!props.disabled">
					<image src="../../static/close.svg" style="width: 50rpx;height: 50rpx;" mode=""></image>
				</view>
			</view>
			<view class="choose" @click="showAction" v-if="files.length<props.size && !props.disabled">
				<view class="add">+</view>
			</view>
		</view>
	</view>
</template>

<script setup lang="ts">
import {ref,watch} from 'vue'
import {FileItem} from './model'

const props = withDefaults(defineProps<{
	modelValue:FileItem[]
	disabled:boolean,
	size:number
}>(),{
	modelValue:() => [],
	disabled:false,
	size:9
})
const emits = defineEmits(['update:modelValue'])
const files = ref<Array<FileItem>>(props.modelValue)

const showAction = () => {
	uni.chooseMedia({
		count: props.size,
		mediaType: ['mix'],
		sourceType: ['album', 'camera'],
		maxDuration: 15,
		camera: 'back',
		success(res) {
			//配置上传接口
			//格式修改
			files.value.push(...res.tempFiles)
		},
		fail(res){
			console.log(res);
		}
	})
}

const preview = (path:string) => {
	let index = files.value.findIndex(i => i.tempFilePath == path)
	let map = files.value.map(e => e.tempFilePath)
	uni.navigateTo({
		url:`/pages/previewMedia/previewMedia?list=${JSON.stringify(files.value)}&current=${index}`
	})
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

watch(
	() => files.value,
	(data) => {
		emits('update:modelValue',data)
	}
)
watch(
	() => props.modelValue,
	(data) => {
		files.value = data
	}
)
</script>

<style scoped lang="less">
.upload{
	width: 90%;
	margin: 0 auto;
	.list{
		width: 100%;
		display: flex;
		justify-content: left;
		flex-wrap: wrap;
		.item,.choose{
			width: 33.3%;
			height: 220rpx;
			display: flex;
			justify-content: center;
			align-items: center;
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
			
			.add{
				width: 98%;
				height: 98%;
				box-sizing: border-box;
				border: 2rpx solid #999;
				display: flex;
				justify-content: center;
				align-items: center;
				font-size: 100rpx;
			}
		}
	}
}
</style>