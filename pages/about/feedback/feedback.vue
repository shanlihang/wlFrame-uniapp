<template>
	<view class="feedback">
		
		<view class="add">
			<wd-form ref="form" :model="addForm">
				<wd-cell-group>
					<wd-cell title-width="170rpx" title="反馈类型" center required>
						<wd-picker align-right :columns="options" v-model="addForm.type"/>
					</wd-cell>
					<wd-cell title-width="170rpx" title="反馈描述" required vertical>
						<wd-textarea
						    clearable
							no-border
							:maxlength="240"
							show-word-limit
						    v-model="addForm.text"
						    placeholder="请输入反馈描述"
						/>
					</wd-cell>
					
				</wd-cell-group>
			</wd-form>
		</view>
		<wd-gap bg-color="#F3F2F7" height="50rpx"></wd-gap>
		<view class="btn">
			<wd-button @click="handleSubmit">提交</wd-button>
		</view>
		<wd-gap bg-color="#F3F2F7" height="40rpx"></wd-gap>
		<view class="history">
			<text @click="showList">反馈历史</text>
		</view>
		
		<wd-action-sheet v-model="flag" title="反馈历史" close-on-click-modal safe-area-inset-bottom @close="close">
			<view style="height: 80vh;padding: 0 24rpx;">
				<card v-for="item in 10" :key="item"/>
				<wd-gap bg-color="#fff" height="50rpx"></wd-gap>
			</view>
			
		</wd-action-sheet>
	</view>
</template>

<script setup lang="ts">
import {ref,reactive} from 'vue'
import card from './components/card.vue'
interface AddForm{
	type:string;
	text:string;
}

const flag = ref<boolean>(false)

const addForm = reactive<AddForm>({
	type:'潜在问题',
	text:''
})

const options = reactive(['潜在问题','新功能需求','改进建议','其他'])

const resetAddForm = () => {
	addForm.type = '潜在问题',
	addForm.text = ''
}

const showList = () => {
	flag.value = true
}

const close = () => {
	flag.value = false
}

const handleSubmit = () => {
	console.log(addForm);
	resetAddForm()
	
}
</script>

<style scoped lang="less">
.feedback{
	width: 100vw;
	height: 100vh;
	.add{
		background-color: #fff;
	}
	.btn{
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.history{
		color: #868686;
		font-size: 24rpx;
		display: flex;
		justify-content: center;
		align-items: center;
	}
}
</style>
