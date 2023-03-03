<template>
	<view class="person-detail-page" :style="theme">
		<button  class="button" @click="themeSet">字体与色调</button>
		<button  class="button" @click="">储存</button>
		<button  class="button" @click="">账号与安全</button>
		<button  class="button" @click="">权限</button>
		<button  class="button" @click="">帮助与反馈</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			themeSet(){
				uni.navigateTo({
					url:'/pages/theme/theme'
				})
			}
		}
	}
</script>

<style>

</style>
