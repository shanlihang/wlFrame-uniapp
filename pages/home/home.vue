<template>
	<view>
		<FloatNav>
			<FloatNavItem url="/pages/index/index" name="首页" />
			<FloatNavItem url="/pages/other/other" name="其他" />
			<FloatNavItem url="/pages/home/home" name="我的" color="#E0E0E0" />
		</FloatNav>
	</view>
</template>

<script lang="ts" setup>
import FloatNav from "../../components/NavBar/floatNav/FloatNav.vue"
import FloatNavItem from "../../components/NavBar/floatNav/FloatNavItem.vue"
</script>

<style>

</style>
