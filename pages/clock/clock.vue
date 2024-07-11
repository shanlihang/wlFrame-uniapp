<template>
	<view class="clock">
		<wd-form ref="form" :model="addForm">
			<wd-cell-group>
				<wd-cell title-width="170rpx" title="打卡标题" center required>
					<wd-input
						no-border
						v-model="addForm.title"
						placeholder="请输入打卡标题"
						align-right
					/>
				</wd-cell>
				<wd-gap bg-color="#F3F2F7" height="2rpx"></wd-gap>
				<wd-cell title-width="170rpx" title="打卡描述" required vertical>
					<wd-textarea
					    clearable
						no-border
						:maxlength="240"
						show-word-limit
					    v-model="addForm.desc"
					    placeholder="请输入打卡描述"
					/>
				</wd-cell>
				<wd-gap bg-color="#F3F2F7" height="2rpx"></wd-gap>
				<wd-cell title-width="170rpx" title="执行周期" required center>
					<wd-calendar
						title="选择执行周期"
						size="small"
						:min-date="new Date()"
						type="daterange"
						v-model="addForm.timeRange"
						align-right
						safe-area-inset-bottom
						@confirm="handleConfirm"
					/>
				</wd-cell>
			</wd-cell-group>
			<wd-gap bg-color="#F3F2F7" height="50rpx"></wd-gap>
			<wd-cell-group>
				<wd-cell title-width="170rpx" title="开启提醒" center>
					<wd-switch v-model="flag" size="24px" active-color="#31AE37" @change="changeFlag" />
				</wd-cell>
				<template v-if="flag">
					<wd-gap bg-color="#F3F2F7" height="2rpx"></wd-gap>
					<wd-cell title-width="170rpx" title="提醒时间" center>
						<wd-datetime-picker type="time" v-model="addForm.time" placeholder="请选择提醒时间" />
					</wd-cell>
				</template>
			</wd-cell-group>
			<view class="tip">
				<wd-icon name="warn-bold" size="12px" color="#a0a0a0"></wd-icon>
				<text style="margin-left: 16rpx;">打卡提醒将在指定日期范围内每日进行提醒</text>
			</view>
			<wd-gap bg-color="#F3F2F7" height="30rpx"></wd-gap>
		</wd-form>
		<view class="btn">
			<wd-button block type="primary" size="large" @click="handleSubmit">创建</wd-button>
		</view>
		
	</view>
</template>

<script setup lang="ts">
import {ref,reactive} from 'vue'
interface AddForm{
	title:string,
	desc:string,
	timeRange:string,
	time:string
}

const form = ref()

const flag = ref<boolean>(false)

const addForm = reactive<AddForm>({
	title:'',
	desc:'',
	timeRange:'',
	time:''
})

const handleConfirm = ({value}) => {
	console.log(value);
}

const handleSubmit = () => {
	console.log(addForm);
	uni.switchTab({
		url:'/pages/index/index'
	})
}

const changeFlag = ({value}) => {
	if(value) return;
	addForm.time = ''
}
</script>

<style scoped lang="less">
.clock{
	width: 100vw;
	height: 100vh;
	.tip{
		padding-left: 24rpx;
		height: 50rpx;
		color: #a0a0a0;
		font-size: 20rpx;
		display: flex;
		align-items: center;
	}
	.btn{
		margin: 0 24rpx;
	}
}

</style>
