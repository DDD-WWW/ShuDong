<template>
  <view class="person-detail-page" :style="theme">
	<view style="display: flex; flex-direction: column;height: 100%;">
		<view style="display: flex;  flex-direction: column;height: 70vh;">
		    <view style="background-color: white;height:20%;border:3rpx solid black; border-radius: 10rpx;padding:10rpx;margin-left: 20px;margin-right: 20px;">标题
		    </view>
		    <view style="background-color:white;height: 80%;margin-top: 20px;border:3rpx solid black; border-radius :10rpx;padding:10rpx; margin-left: 20px;margin-right: 20px;">正文
		    </view>
		</view>
		<view style="display: flex; flex-direction: row; ">
			<button  @click=""><image src="/static/img/like.png"></image>喜欢</button>
			<button  @click=""><image src="/static/img/cheer.png"></image>加油</button>
			<button  @click=""><image src="/static/img/hang.png"></image>拥抱</button>
			<button  @click=""><image src="/static/img/collect.png"></image>收藏</button>
			<button  @click=""><image src="/static/img/share.png"></image> <text>分享</text></button>
		</view>
		<view >
		    <button   @click="load" ><image src="../../static/img/refresh.png"></image>刷新</button>
		</view>
		<view>
		    <button  @click="submit" ><image src="../../static/img/publish.png"></image>投稿</button>
		</view>
	</view>
  </view>
</template>

<script>
	export default {
		
		data() {
			return {
				
			};
		},
		methods :{
			load(){
				uni.redirectTo({
					url:'/pages/index/index'
				})
			},
			submit(){
				uni.navigateTo({
					url:'/pages/submit/submit'
				})
			}
		}
	}
	
</script>

<style>
</style>