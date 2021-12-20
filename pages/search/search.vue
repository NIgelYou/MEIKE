<template>
	<view class="content">
		<view class="top-bar">
			<!-- <image src="../../static/images/img/one.png"></image> -->
			<view class="search-div">
				<image class="search-img" src="../../static/images/search/search.png" mode=""></image>
				<input type="text" value="" v-model="searchInfo" placeholder="搜索用户/群"  class="search"  placeholder-style="color:#aaa;font-weight:400;" 
				@tap="search" />
			</view>
			<view class="top-bar-right">
				<view class="text">
					取消
				</view>
			</view>
		</view>
		<view class="main">
			<view class="search-user result">
				<view class="title">
					用户
				</view>
				<view class="list user">
					<image src="../../static/images/img/one.png" ></image>
					<view class="names">
						<view class="name">
							大力出奇迹
						</view>
						<!-- <view class="email">
							ds@qq.com
						</view> -->
					</view>
					<view class="right-bt">
						发送
					</view>
				</view>
				<view class="list user">
					<image src="../../static/images/img/one.png" ></image>
					<view class="names">
						<view class="name">
							大力出奇迹
						</view>
						<!-- <view class="email">
							ds@qq.com
						</view> -->
					</view>
					<view class="right-bt">
						发送
					</view>
				</view>
				
			</view>
			
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				searchInfo:'',
			}
		},
		methods: {
			search:function(){
				console.log('搜索按鈕按下')
			}
		}
	}
</script>

<style lang="scss">
	@import "../../commons/css/mycss.scss";
	// .content {
	// 	//padding-top: var(--status-bar-height);
	// 	background: #3F536E;
	// }
	.top-bar{
		//padding-top: var(--status-bar-height);
		}
		.search-div{
			//padding-top: var(--status-bar-height);
			//position: absolute;
			float: left;
			top: 0;
			left: 0;
			//width: 100%;
			z-index: -1;
			box-sizing: border-box;
			padding: 14rpx 30rpx 14rpx 16rpx;
		
		.search{
			//width: ;
			//padding-top: var(--status-bar-height);
			//background: #eee;
			float: right;
			padding: 0rpx 120rpx 0rpx 16rpx;
			height: 60rpx;
			background: $uni-bg-color-grey;
			border-radius: 10rpx;
		}
		.search-img{
			//padding-top: var(--status-bar-height);
			//position: absolute;
			float: right;
			right: 60rpx;
			top: 10rpx;
			width: 40rpx ;
			height: 40rpx;
		}
		.top-bar-right{
			//background-color: #eee;
			float: right;
			padding-right: 16rpx;
			//padding-right: $uni-spacing-col-base;
			// padding-left: $uni-spacing-col-base;
			//border: 1px solid red;

			.text{
				font-size: $uni-font-size-lg;
				font-weight: 1000;
				color:$uni-text-color;
				line-height: 88rpx;
				//background: #aaa;
				padding-right:32rpx ;
			}		
		}
	}
	
	.main{
		width: calc(100% - 70rpx);
		padding: 88rpx $uni-spacing-col-base 0 16rpx;
		//padding: 16rpx 0;
		//padding: 88rpx $uni-spacing-col-base 0;
		
		.result{
			padding-top: 32rpx;
			
			.title{
				//position: relative;
				//float: left;
				font-weight: 600;
				font-size: 44rpx;
				color: $uni-text-color;
				line-height: 60rpx;
			}
			// position: relative;
			 //float: left;
			
			// position: relative;
			// float: left;
			.list{
				width: 100%;
				//border: 1px solid red;
				height: 100rpx;
				padding-top: 10rpx;
				//padding: 88rpx $uni-spacing-col-base 0;
				image{
					float: left;
					width: 80rpx;
					height: 80rpx;
					//padding-top: 10rpx;
					border-radius: $uni-border-radius-base;
					background-color: $uni-color-primary;
				}
			}
			
			.names{
				float:left;
				padding-left: $uni-spacing-col-base;
			}
			.name{
				line-height: 25px;
				font-weight: 400;
				font-size: $uni-font-size-base;
				//width: 70px;
				height: 25px;
				font-family: PingFangSC-Regular;
				font-size: 18px;
				color: #272832;
				letter-spacing: -0.62px;
				line-height: 80rpx;
			}
			// .email{
			// 	font-size: $uni-font-size-sm;
			// 	color: $uni-text-color;
			// 	line-height: 50rpx;
			// }
			.right-bt{
				float: right;
				width: 120rpx;
				height: 48rpx;
				background: $uni-color-primary;
				border-radius: 24rpx;
				font-size: $uni-font-size-sm;
				color: $uni-text-color;
				line-height: 48rpx;
				margin-top: 16rpx;
				text-align: center;
				
			}
		}
	}
	// .search-user result{
	// 	padding: 88rpx $uni-spacing-col-base 0;
	// 	height: 96rpx;
	// 	padding: 16rpx 0;
	// }
	// .list{
		
	// }
	
</style>
