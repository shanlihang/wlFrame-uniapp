<template>
	<view class="anniversary">
		<wd-form ref="form" :model="addForm">
			<wd-cell-group>
				<wd-cell title-width="170rpx" title="倒数日标题" center required>
					<wd-input
						no-border
						v-model="addForm.title"
						placeholder="请输入倒数日标题"
						align-right
					/>
				</wd-cell>
				<wd-gap bg-color="#F3F2F7" height="2rpx"></wd-gap>
				<wd-cell title-width="170rpx" title="目标日期" center required>
					<wd-datetime-picker type="date" v-model="addForm.date" :default-value="Date.now()" placeholder="请选择目标日期" />
				</wd-cell>
				<wd-gap bg-color="#F3F2F7" height="2rpx"></wd-gap>
				<wd-cell title-width="170rpx" title="倒数日内容" required vertical>
					<wd-textarea
					    clearable
						no-border
						:maxlength="240"
						show-word-limit
					    v-model="addForm.content"
					    placeholder="请输入倒数日内容"
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
						<wd-datetime-picker v-model="addForm.time" :default-value="Date.now()" placeholder="请选择提醒时间" />
					</wd-cell>
				</template>
				
			</wd-cell-group>
			<wd-gap bg-color="#F3F2F7" height="50rpx"></wd-gap>
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
	content:string,
	date:string,
	time:string
}

const form = ref()

const flag = ref<boolean>(false)

const addForm = reactive<AddForm>({
	title:'',
	content:'',
	date:'',
	time:''
})

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
.anniversary{
	width: 100vw;
	height: 100vh;
	.btn{
		margin: 0 24rpx;
	}
}

</style>

