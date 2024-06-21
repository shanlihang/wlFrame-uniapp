<template>
	<view class="index">
		<view class="header" @click="closeOutside">
			<wd-drop-menu>
				<wd-drop-menu-item v-model="filter.date" :options="dateOptions" @change="handleChangeDate" />
				<wd-drop-menu-item v-model="filter.type" :options="typeOptions" @change="handleChangeType" />
				<wd-drop-menu-item v-model="filter.status" :options="statusOptions" @change="handleChangeStatus" />
			</wd-drop-menu>
		</view>
		
		<view class="add" @click="handleAdd"><wd-icon name="add" size="36px" color="#fff"></wd-icon></view>
	</view>
	
	
</template>


<script setup lang="ts">
import { useQueue } from '@/uni_modules/wot-design-uni'
import {ref,reactive} from 'vue'
import {createToast,createActionSheet} from '../../utils/feedback'

const { closeOutside } = useQueue()

const filter = reactive({
	date:0,
	status:0,
	type:0
})

const dateOptions = reactive([
  { label: '今日', value: 0 },
  { label: '三日内', value: 1 },
  { label: '本周', value: 2 }
])
const statusOptions = reactive([
  { label: '未完成', value: 0 },
  { label: '已完成', value: 1 },
  { label: '全部', value: 2 }
])
const typeOptions = reactive([
  { label: '全部', value: 0 },
  { label: '打卡', value: 1 },
  { label: '代办', value: 2 },
  { label: '倒数日', value: 3 },
])

const handleAdd = () => {
	createActionSheet(['备忘录','打卡','倒数日'],(res) => {
		if(res.tapIndex == 0){
			uni.navigateTo({
				url:'/pages/memo/memo',
			})
		}else if(res.tapIndex == 1){
			uni.navigateTo({
				url:'/pages/clock/clock',
			})
		}else if(res.tapIndex == 2){
			uni.navigateTo({
				url:'/pages/anniversary/anniversary',
			})
		}else{
			createToast("无效操作")
		}
	})
	//消息订阅
	// uni.requestSubscribeMessage({
	//   tmplIds: ['f3KvgxBRSD_lSPoevKMNrSTFdlRW_9gSxcEWDtueqDE','__6qMN8GCplL4pL49X7iwg1eBcGt4Xuygf02jMT0ZRg','WAHNe0zz-VZkvjeMZ4jzVJqaH0LSktfAdYa1oD8vNRc'],
	//   success (res) {
	// 	  console.log(res);
	//   }
	// })
}

function handleChangeDate({ value }) {
  console.log(value)
}
function handleChangeStatus({ value }) {
  console.log(value)
}
function handleChangeType({ value }) {
  console.log(value)
}
</script>

<style lang="less" scoped>
.index {
	width: 100%;
	height: 100vh;
	position: relative;
	.add{
		width: 120rpx;
		height: 120rpx;
		position: absolute;
		bottom: 20rpx;
		right: 20rpx;
		border-radius: 50%;
		background-color: #55aaff;
		display: flex;
		justify-content: center;
		align-items: center;
	}
}
</style>
