<template>
	<view class="about">
		<view class="subMenu">
			<wd-cell v-for="item in menu" :key="item.id" :title="item.name" is-link @click="openDetail(item.path)" />
		</view>
	</view>
</template>

<script setup lang="ts">
import {reactive} from 'vue'
const menu = reactive([
	{id:1,name:'联系我们',path:'/pages/about/contact/contact'},
	{id:2,name:'意见反馈',path:'/pages/about/feedback/feedback'},
	{id:3,name:'用户协议',path:'/pages/about/protocol/protocol'},
	{id:4,name:'隐私政策',path:'/pages/about/policy/policy'},
	{id:5,name:'版本更新',path:'/pages/about/version/version'}
])

const openDetail = (path:string) => {
	uni.navigateTo({
		url:path
	})
}
</script>

<style scoped lang="less">
.about{
	width: 100vw;
	height: 100vh;
}
</style>
