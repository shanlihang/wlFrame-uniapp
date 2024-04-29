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
	width: 100%;
	background-color: #F3F2F7;
	color: #383838;
}
</style>
