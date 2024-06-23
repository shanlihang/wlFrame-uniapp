<template>
	<view class="userInfo">
		<wd-form ref="form" :model="form">
			<wd-cell-group>
				<wd-cell title-width="170rpx" title="头像" center required>
					<wd-img
						:width="100"
						:height="100"
						:src="form.avatar"
					/>
				</wd-cell>
				<wd-cell title-width="170rpx" title="昵称" center required>
					<wd-input
						no-border
						clearable
						v-model="form.nickName"
						placeholder="请输入昵称"
					/>
				</wd-cell>
			</wd-cell-group>
		</wd-form>
		<view class="update">
			<wd-button type="text">修改个人信息</wd-button>
		</view>
		<view class="more">
			<wd-divider>更多操作</wd-divider>
			<view class="action">
				<view class="logout">
					<view class="icon" @click="logout">
						<wd-icon name="logout" size="22px" color="#ff0000"></wd-icon>
					</view>
					<text class="desc">退出登录</text>
				</view>
				<view class="poweroff">
					<view class="icon" @click="poweroff">
						<wd-icon name="poweroff" size="22px" color="#ff0000"></wd-icon>
					</view>
					<text class="desc">注销账号</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script setup lang="ts">
import {reactive} from 'vue'
import {createModal,createToast} from '../../utils/feedback'
interface Form{
	avatar:string,
	nickName:string
}

const form = reactive<Form>({
	avatar:'../../static/noAvatar.png',
	nickName:'asfasfasfas'
})

const logout = () => {
	createModal('退出提示','请问您确定要退出账号吗？',(res) => {
		if(res.confirm){
			createToast('确认退出')
		}
	})
}

const poweroff = () => {
	createModal('注销提示','注销账号将清空所有历史数据，请问您确定要注销账号吗？',(res) => {
		if(res.confirm){
			createToast('确认注销')
		}
	})
}
</script>

<style scoped lang="less">
.userInfo{
	width: 100vw;
	height: 100vh;
	position: relative;
	.update{
		height: 100rpx;
		line-height: 100rpx;
		text-align: center;
	}
	.more{
		width: 100%;
		position: absolute;
		bottom: 100rpx;
		.action{
			display: flex;
			margin-top: 20rpx;
			align-items: center;
			justify-content: center;
			.logout,.poweroff{
				width: 100rpx;
				display: flex;
				flex-direction: column;
				align-items: center;
				.icon{
					width: 70rpx;
					height: 70rpx;
					margin-bottom: 10rpx;
					border-radius: 50%;
					display: flex;
					justify-content: center;
					align-items: center;
					background-color: #fff;
				}
				.desc{
					font-size: 16rpx;
					color: #a0a0a0;
				}
			}
		}
	}
}
</style>
