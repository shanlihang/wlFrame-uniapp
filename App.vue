<script setup lang="ts">
import {onLaunch,onHide} from '@dcloudio/uni-app'
import { reactive } from 'vue';
// import {ThemeOption} from './model/app'

const themeOption = reactive({
	pageBgColor:'#282828',
	boxBgColor:'#494949',
	primaryColor:'#34e1f6',
	infoColor:'#A0A0A0',
	warnColor:'#ff0000',
	mainFontColor:'#E0E0E0',
	subFontColor:'#fff',
	mainFontSize:'24rpx',
	subFontSize:'18rpx'
})

onLaunch(() => {
	console.log('App Launch')
})

onHide(() => {
	console.log('App Hide')
}) 
</script>

<style>
<<<<<<< HEAD
	/*每个页面公共css */
	page{
		background-color: v-bind(themeOption.boxBgColor);
	}
=======
>>>>>>> b3991cc89cfef9b1626fbfc5b62881acad2ad1c3
</style>
