<template>
	<view class="feedback-card">
		<view class="header">
			<wd-tag type="warning" plain>标签</wd-tag>
			<view>2024-06-23 15:37</view>
		</view>
		<view class="main">
			<view class="type">反馈类型：其他</view>
			<view class="desc">反馈描述：发i就是发哦师范类是否能拉是否能拉克丝贝纳颂反馈历史凡是你疯啦  </view>
			<view class="handle">处理详情：不是福布斯发布时间可否把开始</view>
		</view>
	</view>
</template>

<script lang="ts" setup>

</script>

<style scoped lang="less">
.feedback-card{
	width: 100%;
	border-radius: 6rpx;
	background-color: #f1f1f1;
	margin-bottom: 24rpx;
	.header{
		padding: 0 20rpx;
		height: 50rpx;
		border-bottom: 2rpx solid #fff;
		display: flex;
		align-items: center;
		justify-content: space-between;
		font-size: 20rpx;
	}
	.main{
		font-size: 24rpx;
		padding: 12rpx 30rpx;
	}
}
</style>