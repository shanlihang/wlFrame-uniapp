<template>
	<view class="err">
		<PageNotFound v-if="flag == '0001'" />
		<NetWorkWarn v-else-if="flag == '0002'" />
		<OtherWarn v-else />
		<wd-button type="warning" @click="lastPage">返回上一页</wd-button>
	</view>
</template>

<script setup lang="ts">
import {ref} from 'vue'
import {onLoad} from '@dcloudio/uni-app'
import PageNotFound from './components/PageNotFound/PageNotFound.vue'
import NetWorkWarn from './components/NetWorkWarn/NetWorkWarn.vue'
import OtherWarn from './components/OtherWarn/OtherWarn.vue'

const flag = ref<string>('')

const lastPage = () => {
	uni.navigateBack()
}

onLoad((option) => {
	flag.value = option.code;
})
</script>

<style scoped lang="less">
.err{
	width: 100%;
	height: 80vh;
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	justify-content: center;
}
</style>
