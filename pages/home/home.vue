<template>
	<view class="index">
		<view class="bk-img">
			<wd-img
				width="100%"
				height="400rpx"
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
						src="../../static/noAvatar.png"
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
			<view class="menu">
				<view class="item" v-for="item in menuList">
					<view class="title">{{item.name}}</view>
					<view class="icon">
						<wd-icon name="arrow-right" color="#A0A0A0" size="22px"></wd-icon>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>


<script setup lang="ts">
import { reactive } from 'vue';
	
const menuList = reactive([
	{id:1,name:'个人资料',path:''},
	{id:2,name:'联系客服',path:''},
	{id:3,name:'意见反馈',path:''},
	{id:4,name:'系统设置',path:''},
])

</script>

<style lang="less" scoped>
.index {
	width: 100%;
	.bk-img{
		width: 100%;
		height: 400rpx;
		overflow: hidden;
	}
	.box{
		width: 100%;
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
				border: 6rpx solid #E0E0E0;
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
		.menu{
			margin: 0 16rpx;
			margin-top: 20rpx;
			border-radius: 9rpx;
			overflow: hidden;
			background-color: #fff;
			.item{
				margin: 0 24rpx;
				height: 80rpx;
				display: flex;
				align-items: center;
				justify-content: space-between;
				border-bottom: 2rpx solid #E0E0E0;
			}
			.item:last-child{
				border: 0;
			}
		}
	}
}
</style>
