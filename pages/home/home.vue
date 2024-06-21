<template>
	<view class="home">
		<view class="bk-img">
			
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
			<view class="app">
				<view class="title">
					<view class="main">应用推荐</view>
					<view class="sub">更多精彩应用持续开发中</view>
				</view>
				<view class="apps">
					<view class="item" v-for="item in apps" :key="item.id">
						<wd-icon :name="item.icon" size="32px" color="#55aaff"></wd-icon>
						<text>{{item.name}}</text>
					</view>
				</view>
			</view>
			<view class="menu">
				<view class="item" v-for="item in menuList.base">
					<view class="title">{{item.name}}</view>
					<view class="icon">
						<wd-icon name="arrow-right" color="#A0A0A0" size="22px"></wd-icon>
					</view>
				</view>
			</view>
			<view class="menu">
				<view class="item" v-for="item in menuList.contact">
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
	
const menuList = reactive({
	base:[
		{id:1,name:'个人资料',path:''},
		{id:2,name:'系统主题',path:''},
		{id:3,name:'意见反馈',path:''},
		{id:4,name:'系统设置',path:''},
	],
	contact:[
		{id:1,name:'帮助中心',path:''},
		{id:2,name:'用户协议',path:''},
		{id:3,name:'隐私政策',path:''},
		{id:4,name:'关于我们',path:''},
	]
})

const apps = reactive([
	{id:1,name:'github',icon:'github-filled'},
	{id:2,name:'chorme',icon:'chrome-filled'}
])

</script>

<style lang="less" scoped>
.home {
	width: 100%;
	.bk-img{
		width: 100%;
		height: 400rpx;
		overflow: hidden;
		background-color: aqua;
	}
	.box{
		width: 100%;
		padding-bottom: 100rpx;
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
		.app{
			margin: 20rpx 16rpx;
			height: 200rpx;
			background-color: #fff;
			border-radius: 6rpx;
			.title{
				padding: 0 24rpx;
				height: 70rpx;
				display: flex;
				justify-content: space-between;
				align-items: center;
				font-weight: bold;
				font-size: 32rpx;
				.sub{
					font-size: 20rpx;
					color: #bdbdbd;
				}
			}
			.apps{
				height: 130rpx;
				display: flex;
				align-items: center;
				.item{
					width: 100rpx;
					height: 100rpx;
					margin-left: 36rpx;
					border-radius: 6rpx;
					background-color: #E1F3FF;
					display: flex;
					flex-direction: column;
					justify-content: center;
					align-items: center;
					font-size: 16rpx;
				}
			}
		}
		.menu{
			margin: 0 16rpx 24rpx;
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
