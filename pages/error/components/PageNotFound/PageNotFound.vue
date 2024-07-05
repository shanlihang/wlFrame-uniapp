<template>
	<view class="PageNotFound">
		<view class="icon">
			<wd-icon name="warning" size="80px"></wd-icon>
		</view>
		<view class="msg">您访问的页面不存在</view>
	</view>
</template>

<script setup lang="ts">

</script>

<style scoped lang="less">
.PageNotFound{
	width: 100%;
	display: flex;
	flex-direction: column;
	align-items: center;
	.icon{
		width: 300rpx;
		height: 300rpx;
		display: flex;
		align-items: center;
		justify-content: center;
		border-radius: 50%;
		border: 2rpx solid #dadada;
	}
	.msg{
		height: 100rpx;
		line-height: 100rpx;
		text-align: center;
	}
}
</style>