<template>
  <view class="person-detail-page" :style="theme">
	<view class="share" style="display: flex; flex-direction: column;">
		 <view class="choose">
		     <picker :range="weathers" @change="weatherChange" mode="multiSelector">
		        状态：{{  weathers[0][weathersIndex1] }}  天气: {{ weathers[1][weathersIndex2]  }}
		     </picker>
		 </view>
		<!-- 标题输入框 -->
		<view class="uni-textarea">
			<textarea placeholder-style="color:#AAAAAA" placeholder="标题..." @input="bindTextAreaInput" />
		</view>
		
		<!-- 标题发布 -->
		<view class="pics">
			<view class="medias" v-for="( image, index ) in uploadPicsList" :key="index">
			  <image
				class="img"
				:src="image.path"
				:data-src="image"
				@tap="previewImage(index)"
				mode="aspectFill"
			  />
			 <view @tap="removeImage(index)"></view> 
			</view>
		</view>
		<!-- 正文发布 -->
		<view class="uni-textareas">
			<textarea placeholder-style="color:#AAAAAA" placeholder="正文..." @input="bindTextAreaInput" />
		</view>
		
		<!-- 正文发布 -->
		<view class="pics">
			<view class="medias" v-for="( image, index ) in uploadPicsList" :key="index">
			  <image
				class="img"
				:src="image.path"
				:data-src="image"
				@tap="previewImage(index)"
				mode="aspectFill"
			  />
			 <view @tap="removeImage(index)"></view> 
			</view>
		
			<!-- 选择照片按钮 -->
			<view class="uploadBtn" @tap="chosePicsAndUpload" v-if="uploadPicsList.length < 9">
			  <view class="text">选择照片</view>
			</view>
		
		</view>

		<view>
		  <button class="button" @click="sendFeed" :disabled="uploadStatus">发布</button>
		</view>

    </view>
  </view>
</template>
<script>
	export default {
		data() {
			return {
			  // 发布内容描述
			  feedInfo: "",
			  // 预置图片上传列表
			  uploadPicsList: [],
			  // 发布状态控制器
			  uploadStatus: false,
			  weathers:[
			      ["状态", "开心" ,"悲伤" ,"愤怒"],
			      ["天气", "晴天" ,"雨天" ,"阴天"]
			  ],
			  weathersIndex1: 0,
			  weathersIndex2: 0
			}
		},
		methods: {
			weatherchange:function(e){
			    console.log(e)
			    //获得对象的 detail的 value
			    //通过数组的下标改变显示在页面的值
			    this.weathersIndex1 = e.detail.value[0];
			    this.weathersIndex2 = e.detail.value[1];
			},
			// textarea 输入内容获取
			bindTextAreaInput(e) {
			  this.feedInfo = e.detail.value;
			},
			// 选择并上传图片
			chosePicsAndUpload() {
			  let count = 9 - this.uploadPicsList.length;
			  if (this.uploadPicsList.length >= 9) {
			    uni.showToast({
			      title: "最多选择9张照片",
			      icon: "success",
			      duration: 1000,
			    });
			    count = 0;
			    return false;
			  }
			  uni.chooseImage({
			    count, //默认9
			    sizeType: ["compressed"], //可以指定是原图还是压缩图，默认二者都有
			    sourceType: ["album", "camera"], //从相册选择
			    success: (res) => {
			      this.uploadPicsList = [...this.uploadPicsList, ...res.tempFiles];
			      if (this.uploadPicsList.length > 9) {
			        this.uploadPicsList = this.uploadPicsList.slice(0, 9);
			      }
			    },
			  });
			},
			// 预览图片
			previewImage(index) {
			  //预览图片
			  var current = this.uploadPicsList[index].path;
			  let urls = [];
			  this.uploadPicsList.map((item) => {
			    urls.push(item.path);
			  });
			  uni.previewImage({
			    current: current,
			    urls,
			  });
			},
			// 删除图片
			removeImage(index) {
			  this.uploadPicsList.splice(index, 1);
			},
			// 发布动态
			async sendFeed() {
			  // 如果正在上传中则等待
			  if (this.uploadStatus) return
			  this.uploadStatus = true
			  
			  // 如果描述为空则不进行发布
			  if (this.feedInfo == "") {
			    uni.showToast({
			      title: "描述不能为空",
			      icon: "loading",
			      duration: 1000,
			    })
			    this.uploadStatus = false
			    return
			  }

			  if (this.uploadPicsList.length <= 0) {
			    uni.showToast({
			      title: "请选择照片",
			      icon: "loading",
			      duration: 1000,
			    })
			    this.uploadStatus = false
			    return
			  }
			  
			  uni.showToast({
			    title: "动态发布中...",
			    icon: "loading",
			    duration: 60000,
			  });
			  
			}
		}
	}
</script>
<style lang="scss" scoped>
	.share {
		width: 750upx;
		margin-top: 20upx;
		margin-bottom: 200upx;
	}

	.choose {
		margin: 20upx 50upx;
		padding: 20upx;
		border-radius: 10upx;
		border: 1upx solid #ccc;
		height: 50rpx;
	}
	.uni-textarea {
		margin: 20upx 50upx;
		padding: 20upx;
		border-radius: 10upx;
		border: 1upx solid #ccc;
		height: 100rpx;
	}
	.uni-textareas {
		margin: 20upx 50upx;
		padding: 20upx;
		border-radius: 10upx;
		border: 1upx solid #ccc;
	}

	.pics {
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: flex-start;
		align-items: center;
		align-content: center;
		padding-top: 20upx;
		padding-bottom: 20upx;
		padding-left: 46upx;
		

		.medias {
			width: 210upx;
			height: 210upx;
			background-color: #eee;
			border-radius: 6upx;
			margin: 5upx;
			position: relative;

			.iclose {
				position: absolute;
				right: 0;
				top: 0;
				background-color: rgba($color: #333, $alpha: 0.6);
				border-bottom-left-radius: 100%;
				padding: 10upx 10upx 16upx 16upx;
				z-index: 999;
			}
		}

		.img {
			width: 210upx;
			height: 210upx;
			border-radius: 6upx;
		}
		
		.imgs {
			width: 210upx;
			height: 70upx;
			border-radius: 6upx;
		}

		.video {
			width: 210upx;
			height: 210upx;
			border-radius: 6upx;
		}

		.uploadBtn {
			width: 210upx;
			height: 210upx;
			background-color: #eee;
			border-radius: 6upx;
			margin: 5upx;
			display: flex;
			flex-direction: column;
			flex-wrap: wrap;
			justify-content: center;
			align-items: center;
			align-content: center;
			
		   .text {
			color: #888;
			font-size: 24upx;
			margin-top: 20upx;
		   }	
	    }
	}
</style>
