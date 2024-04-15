<!-- 
	需要的props
	color:					字体及图标的颜色
	url：					跳转路径
	name:					菜单项名称
 -->
<template>
	<view class="floatNavItem">
		<navigator :url="props.url">
			<view class="icon">
				<wd-icon name="home" size="30px" :color="props.color" />
			</view>
			<view class="font" :style="{color:props.color}">
				<text>{{props.name}}</text>
			</view>
		</navigator>
	</view>
</template>

<script setup lang="ts">
interface FloatNavItem{
	color?:string,
	url:string,
	name?:string
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