<template>
	<view class="plan">
		<button @click="open('/pages/login/login')">登录</button>
		<button @click="open('/pages/avatarAndName/avatarAndName')">选择头像昵称</button>
		<button @click="open('/pages/a/a')">跳转不存在的页面</button>
		<button @click="open('/pages/error/error')">不存在的页面</button>
	</view>
</template>


<script setup lang="ts">

const open = (url:string) => {
	uni.navigateTo({
		url:url
	})
}
</script>

<style lang="less" scoped>
.plan {
	width: 100%;
	height: 100vh;
}
</style>
