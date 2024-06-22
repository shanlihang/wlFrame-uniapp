<template>
	<view class="contact">
		<view class="action">
			<view style="width: 200rpx;text-align: center;color: #868686;">快捷操作 :</view>
			<wd-tag round style="margin-right: 20rpx;" @click="handleDial">拨打电话</wd-tag>
			<view class="gap"></view>
			<wd-tag round @click="addContact">保存到通讯录</wd-tag>
		</view>
		<wd-cell v-for="item in data" :key="item.id" :title="item.title" :value="item.value" clickable @click="handleCopy(item.value)" />
	</view>
</template>

<script setup lang="ts">
import {reactive} from 'vue'
import {createToast} from '../../../utils/feedback'

const data = reactive([
	{id:1,title:'电话',value:'18348563173',isPhone:true},
	{id:2,title:'qq',value:'67490009',isPhone:false},
	{id:3,title:'微信',value:'slh09091025',isPhone:false},
	{id:4,title:'邮箱',value:'slh67490009@gmail.com',isPhone:false}
])

const handleCopy = (value:string) => {
	uni.setClipboardData({
		data: value,
		success: () => {
			createToast('信息已复制')
		},
		fail: () => {
			createToast('复制失败，请重试')
		}
	});
}

const handleDial = () =>{
    let phone = ''
	data.map(e => {
		if(e.isPhone){
			phone = e.value
		}
	})
	uni.makePhoneCall({
		phoneNumber: phone,
	});
	
}

const addContact = () => {
	let phone = ''
	data.map(e => {
		if(e.isPhone){
			phone = e.value
		}
	})
	uni.addPhoneContact({
		lastName: '官方',
		firstName: '掌时记',
		mobilePhoneNumber: phone,
	});
}

</script>

<style scoped lang="less">
.contact{
	width: 100vw;
	height: 100vh;
	.action{
		font-size: 24rpx;
		height: 80rpx;
		display: flex;
		align-items: center;
		.gap{
			width: 30rpx;
			height: 80rpx;
		}
	}
}
</style>
