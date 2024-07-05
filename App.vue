<script setup lang="ts">
import {onLaunch,onHide,onThemeChange} from '@dcloudio/uni-app'
onThemeChange((option) => {
	console.log(option.theme)
})
onLaunch(() => {
	console.log('应用初始化')
})

onHide(() => {
	console.log('应用切换后台')
}) 

</script>

<style>
page{
	box-sizing: border-box;
	background-color: #F3F2F7;
	color: #383838;
}
</style>
