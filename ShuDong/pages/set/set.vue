<template>
	<view class="person-detail-page" :style="theme">
		<button  class="button" >关于树洞</button>
		<button  class="button" >检查更新</button>
		<button v-if="isLogin" class="button" @click="loginOut">登出</button>
		<button  class="button" @click="themeSet">应用设置</button>
	</view>
</template>

<script>
	export default {
		
		computed:{
			isLogin(){
				const isLogin = this.$store.state.isLogin;
				if(!isLogin){
					uni.redirectTo({
						url:'/pages/login/login'
					})
				}
				return isLogin;
			}
		},
		data() {
			return {
				
			}
		},
		onLoad() {

		},
		methods: {
			loginOut(){
				this.$store.commit('update',['isLogin',false]);
			},
			
		    themeSet(){
			   uni.navigateTo({
			   url:'/pages/applicationSet/applicationSet'
			   });
			},			
        }
}
</script>

<style lang="scss" scoped>
	
</style>
