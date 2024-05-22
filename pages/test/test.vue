<template>
	<view class="test">
		<UploadMedia v-model="list"/>
	</view>
</template>

<script setup lang="ts">
import UploadMedia from '../../components/UploadMedia/UploadMedia.vue'
import {ref} from 'vue'

const list = ref([])
</script>

<style scoped lang="less">
.test{
	height: 100vh;
}
</style>
