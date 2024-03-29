<!-- 
	需要的props
	color:					字体及图标的颜色
 -->
<template>
	<view class="floatNavItem">
		<view class="icon">
			<wd-icon name="home" size="30px" :color="props.color" />
		</view>
		<view class="font" :style="{color:props.color}">
			<text>首页</text>
		</view>
	</view>
</template>

<script setup lang="ts">
interface FloatNavItem{
	color?:string
}

const props = withDefaults(defineProps<FloatNavItem>(),{
	color:"#999"
})
</script>

<style scoped lang="less">
.floatNavItem{
	height: 100rpx;
	width: 20%;
	display: flex;
	flex-direction: column;
	justify-content: center;
	.icon{
		width: 100%;
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.font{
		width: 100%;
		font-size: 16rpx;
		display: flex;
		align-items: center;
		justify-content: center;
	}
}
</style>