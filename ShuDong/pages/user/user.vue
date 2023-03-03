<template>
	<view class="person-detail-page" :style="theme">
		<button  class="button" @click="submission">我的投稿</button>
		<button  class="button" @click="letterBox">信箱</button>
		<button  class="button" @click="collect">收藏</button>
		<button  class="button" @click="set">设置</button>
	</view>
</template>

<script>
	export default {
			
		data() {
			return {
				
			}
		},
		onLoad() {

		},
		methods: {
			set(){
				uni.navigateTo({
					url:'/pages/set/set'
				})
				
			},
			submission(){
				uni.navigateTo({
					url:'/pages/submission/submission'
					
				})
			},
			letterBox(){
				uni.navigateTo({
					url:'/pages/letterBox/letterBox'
					
				})
			},
			collect(){
				uni.navigateTo({
					url:'/pages/collect/collect'
					
				})
			}
			
		}
	}
</script>

<style lang="scss" scoped>
	
</style>