<template>
	<view class="index">
		<view class="bk-img">
			<wd-img
				width="100%"
				height="500rpx"
				src="../../static/test.jpg"
				:enable-preview="true"
			/>
		</view>
		<view class="box">
			<view class="info">
				<view class="avatar">
					<wd-img
						width="150rpx"
						height="150rpx"
						src="../../static/logo.png"
						:enable-preview="true"
					/>
				</view>
				<view class="name">
					<text class="title">昵称</text>
					<text>ID：1656651685165154</text>
				</view>
				<view class="score">
					123456
				</view>
			</view>
		</view>
	</view>
</template>


<script setup lang="ts">

</script>

<style lang="less" scoped>
.index {
	width: 100%;
	position: relative;
	.bk-img{
		width: 100%;
		height: 500rpx;
		overflow: hidden;
	}
	.box{
		width: 100%;
		height: 1500rpx;
		.info{
			margin: 0 16rpx;
			height: 200rpx;
			display: flex;
			align-items: center;
			position: relative;
			.avatar{
				width: 150rpx;
				height: 150rpx;
				overflow: hidden;
				border-radius: 50%;
			}
			.name{
				flex: 1 0 auto;
				margin-left: 20rpx;
				height: 150rpx;
				font-size: 30rpx;
				display: flex;
				flex-direction: column;
				justify-content: space-evenly;
				.title{
					font-size: 40rpx;
					font-weight: bold;
				}
			}
			.score{
				position: absolute;
				right: 10rpx;
				padding: 4rpx;
				border: 2rpx solid orange;
				border-radius: 6rpx;
				background-color: orange;
				font-size: 20rpx;
			}
		}
	}
}
</style>
