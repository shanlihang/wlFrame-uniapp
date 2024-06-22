<template>
	<view class="memo">
		<wd-form ref="form" :model="addForm">
			<wd-cell-group border>
				<wd-cell title="备忘录标题" center required>
					<wd-input
						no-border
						clearable
						v-model="addForm.title"
						placeholder="请输入备忘录标题"
					/>
				</wd-cell>
				<wd-cell title="备忘录内容" required vertical>
					<wd-textarea
					    clearable
						no-border
						:maxlength="240"
						show-word-limit
					    v-model="addForm.content"
					    placeholder="请输入备忘录内容"
					/>
				</wd-cell>
				
			</wd-cell-group>
			<wd-gap bg-color="#F3F2F7" height="50rpx"></wd-gap>
			<wd-cell-group>
				<wd-cell title="提醒时间" label="不设置提醒时间则不进行消息提醒" center>
					<wd-datetime-picker v-model="addForm.time" :default-value="Date.now()" />
				</wd-cell>
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
	time:string
}

const form = ref()

const addForm = reactive<AddForm>({
	title:'',
	content:'',
	time:''
})

const handleSubmit = () => {
	console.log(addForm);
}
</script>

<style scoped lang="less">
.memo{
	width: 100vw;
	height: 100vh;
	.btn{
		margin: 0 24rpx;
	}
}
</style>
