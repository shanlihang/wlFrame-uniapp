<script setup lang="ts">
import {onLaunch,onHide} from '@dcloudio/uni-app'

onLaunch(() => {
	console.log('App Launch')
})

onHide(() => {
	console.log('App Hide')
}) 
</script>

<style>
page{
	box-sizing: border-box;
	background-color: #F3F2F7;
	color: #383838;
}
</style>
