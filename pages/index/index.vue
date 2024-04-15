<template>
<<<<<<< HEAD
	<view class="a">
		<FloatNav></FloatNav>
=======
	<view class="index">
		<FloatNav>
			<FloatNavItem url="/pages/index/index" name="首页" color="#E0E0E0" />
			<FloatNavItem url="/pages/other/other" name="其他" />
			<FloatNavItem url="/pages/home/home" name="我的" />
		</FloatNav>
>>>>>>> b3991cc89cfef9b1626fbfc5b62881acad2ad1c3
	</view>
</template>


<script setup lang="ts">
import {onLoad,onPullDownRefresh} from "@dcloudio/uni-app"
import {ref} from "vue"
import FloatNav from "../../components/NavBar/floatNav/FloatNav.vue"
import FloatNavItem from "../../components/NavBar/floatNav/FloatNavItem.vue"

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
