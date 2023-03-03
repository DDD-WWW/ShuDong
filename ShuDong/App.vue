<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>


<style lang="scss">
	/*每个页面公共css */
	button::after{
		border: none;
	}
	button{
	  padding: 0;
	  background-color: transparent;    
	  border:none;				
	  width: 100rpx;
	  height: 100rpx;
	  margin:0 30upx;
	  border-radius:50upx;
	  line-height: 80upx;
	  font-size: 32upx;
	  margin-top: 20px;
	  margin-left:auto;
	  margin-right:auto;
	}
	button image{
	  width: 100rpx;
	  height: 100rpx;
	}
	
	uni-page-body {
	  height: 100%;
	}
	.page {
	  width:100%;
	  height:100%;
	  background-image: url(/static/img/timg.jpg);
	  background-repeat: no-repeat;
	  background-size:100% 100%;
	}
	.person-detail-page {
	  background-color: $theme-bg;
	  color: $theme-color;
	  height: 100%;
	}
	
	
	
	.info-list {
	  .baseInfo {
	    padding: 0rpx 15px;
	
	    .item {
	      display: flex;
	      align-items: center;
	      justify-content: space-between;
	      padding: 35rpx 0rpx;
	      border-bottom: 1px solid #e8e8e8;
	      .label {
	        flex-shrink: 0;
	        margin-right: 50rpx;
	      }
	    }
	  }
	}
	.input-box {
		padding: 50upx;
		font-size: 30upx;
		.input-item {
			display: flex;
			border-bottom: 1upx solid #eeeeee;
			line-height: 100upx;
			height: 100upx;
			color: rgb(255,255,255);
			.input-label {
				width: 150upx;
			}
			.input-body{
				position: relative;
				height: 100upx;
				width: calc(100% - 150upx);
				.input {
					line-height: 100upx;
					height: 100upx;
					position: relative;
					font-size: 28upx;
				}
				.eye{
					position: absolute;
					height: 50upx;
					width: 50upx;
					right: 0;
					top: 50%;
					transform: translateY(-50%);
				}
				.btn-code{
				    position: absolute;
				    right: 0upx;
				    top:50%;
				    transform: translateY(-50%);
					background: none;
					color: #205592;
					width: 160upx;
					font-size: 24upx;
					box-sizing: border-box;
					text-align: right;
					padding: 0;
					height: 100upx;
					line-height: 100upx;
				}
			}
			
		}
		.select {
			padding-top: 40upx;
			display: flex;
			justify-content: right;
			color:  rgb(255,255,255);
			
		}
		
	}
	.login{
		   display: flex;
		   align-items: center;
		   justify-content: center;
		   color:  rgb(255,255,255);
		   margin-top: 20px;
	}
	
	.button{
		margin:0 30upx;
		background: #0dbf8c;
		border-radius:50upx;
		line-height: 80upx;
		height: 80upx;
		width: 240upx;
		color: white;
		font-size: 32upx;
		margin-top: 20px;
		margin-left:auto;
		margin-right:auto;
	}
	
</style>
