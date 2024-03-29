<template>
	<view class="index">
		<FloatNav></FloatNav>
	</view>
</template>


<script setup lang="ts">
import {onLoad,onPullDownRefresh} from "@dcloudio/uni-app"
import {ref} from "vue"
import FloatNav from "../../components/NavBar/floatNav/FloatNav.vue"

const btnText = ref<string>('成功按钮')

onLoad(() => {})

onPullDownRefresh(() => {
	setTimeout(() => {
		btnText.value = '已刷新'
	},2000)
	
	uni.stopPullDownRefresh()
})
</script>

<style lang="less" scoped>
.index {
	width: 100%;
	height: 100vh;
}
</style>
