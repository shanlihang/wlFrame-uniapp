<template>
	<view class="version">
		<wd-cell-group border>
			<wd-cell v-for="item in data" :key="item.id" :title="'日程助 '+item.version+' 更新'" :label="item.date" size="large" center isLink @click="showDetail(item.content)"></wd-cell>
		</wd-cell-group>
		<wd-action-sheet v-model="flag" title="版本更新详情" close-on-click-modal safe-area-inset-bottom @close="close">
			<view style="height: 800rpx;padding: 0 24rpx;">{{temp}}</view>
		</wd-action-sheet>
	</view>
</template>

<script setup lang="ts">
import {ref,reactive} from 'vue'

const flag = ref<boolean>(false)
const temp = ref<string>('')

const data = reactive([
	{id:1,version:'1.0.0',date:'2024-04-11',content:'123165161561616156163'},
	{id:2,version:'1.0.1',date:'2024-04-15',content:'暗杀撒撒发生的纷扰是'},
	{id:3,version:'1.0.2',date:'2024-04-19',content:'123165161沙发上发发生发生561616156163'},
	{id:4,version:'1.2.0',date:'2024-04-21',content:'gadsfgasfgasfgasfgefefaedfefaefaef'},
])

const showDetail = (content:string) => {
	flag.value = true
	temp.value = content
}

const close = () => {
	temp.value = ''
}

</script>

<style scoped lang="less">
.version{}
</style>
