<!-- 
	需要的props
	backgroundColor:		导航栏背景色
	borderRadius:			导航栏圆角
 -->
<template>
	<view class="floatNav">
		<view class="nav" :style="{
			backgroundColor:props.backgroundColor,
			borderRadius:props.borderRadius,
		}">
			<FloatNavItem></FloatNavItem>
			<FloatNavItem></FloatNavItem>
			<FloatNavItem></FloatNavItem>
		</view>
	</view>
</template>

<script lang="ts" setup>
import FloatNavItem from "./FloatNavItem.vue"
interface FloatNav{
	backgroundColor?:string,
	borderRadius?:string,
}

const props = withDefaults(defineProps<FloatNav>(),{
	backgroundColor:"rgba(0, 0, 0, 0.3)",
	borderRadius:"48rpx",
})

</script>

<style scoped lang="less">
.floatNav{
	width: 100%;
	position: absolute;
	bottom: 5%;
	.nav{
		width: 80%;
		height: 100rpx;
		margin: 0 auto;
		display: flex;
		align-items: center;
		justify-content: space-evenly;
	}
	
}
</style>