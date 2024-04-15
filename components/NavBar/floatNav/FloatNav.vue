<!-- 
	需要的props
	backgroundColor:		导航栏背景色
	borderRadius:			导航栏圆角
	bottom:					距底距离
 -->
<template>
	<view class="floatNav" :style="{bottom:'5%'}">
		<view class="nav" :style="{
			backgroundColor:props.backgroundColor,
			borderRadius:props.borderRadius,
		}">
			<slot></slot>
		</view>
	</view>
</template>

<script lang="ts" setup>
import FloatNavItem from "./FloatNavItem.vue"
interface FloatNav{
	backgroundColor?:string,
	borderRadius?:string,
	bottom?:string
}

const props = withDefaults(defineProps<FloatNav>(),{
	backgroundColor:"rgba(0, 0, 0, 0.3)",
	borderRadius:"48rpx",
	bottom:'5%'
})

</script>

<style scoped lang="less">
.floatNav{
	width: 100%;
	position: absolute;
	// bottom: 5%;
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