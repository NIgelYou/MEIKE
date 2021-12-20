<template>
	<view class="content">
		<view class="top-bar">
			<view class="top-bar-left">
				<!-- <image src="../../static/images/img/one.png"></image> -->
			</view>
			
			<view class="top-bar-center">
				<!-- <image src="../../static/images/index/logo.png"  class="logo"></image> -->
				
				<view class="title-name">
					
				</view>
			</view>
			
			<view class="top-bar-right">
				<view class="search"><image src="../../static/images/index/search.png" ></image></view>
				<view class="add"><image src="../../static/images/index/add.png" ></image></view>
			</view>
			
		</view>
		<view class="main">
			<view class="friends">
				<view class="friend-list" v-for="(item,index) in friends" :key="index">
					<view class="friend-list-l">
						<text class="tip" v-if="item.tip>0">{{item.tip}}</text>
						<image :src="item.imgurl" ></image>
					</view>
					<view class="friend-list-r">
						<view class="top">
							<view class="name">
								{{item.name}}
							</view>
							<view class="time">
								{{changeTime(item.time)}}
							</view>
						</view>
						<view class="news">
							{{item.news}}
						</view>
					</view>
				</view>
			</view>
			<view class="friends">
				<view class="friend-list" >
					<view class="friend-list-l">
						<text class="tip">1</text>
						<image src="../../static/images/img/one.png" ></image>
					</view>
					<view class="friend-list-r">
						<view class="top">
							<view class="name">
								都知
							</view>
							<view class="time">
								13:43
							</view>
						</view>
						<view class="news">
							[content;substance] 事物所包含的实质性事物
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import datas from '../../commons/js/datas.js'
	import myfun from '../../commons/js/myfun.js'
	export default {
		data() {
			return {
				friends:[],
			}
		},
		onLoad() {
			this.getFriends()
		},
		
		methods: {
			changeTime: function(date){
				return myfun.dateTime(date)
			},
			getFriends: function(){
				this.friends = datas.friends();
				for(let i=0 ;i<this.friends.length;i++)
				this.friends[i].imgurl='../../static/images/img/' + this.friends[i].imgurl;
				console.log(this.friends)
			}
		}
	}
</script>
<style lang="scss">
	@import "../../commons/css/mycss.scss";
	.top-bar{
		background: rgba(255,255,255,0.96);
	}
	.top-bar-left{
	}
	.top-bar-center{
	}
	.top-bar-right{
	}
	.main{
		padding-top: 80rpx ;
		//border: 1px solid red;
	}
	.friend-list{
		padding: 88rpx $uni-spacing-col-base 0;
		height: 96rpx;
		padding: 16rpx 0;
		.friend-list-l{
			position: relative;
			float: left;
			image{
				width: 96rpx;
				height: 96rpx;
				border-radius: $uni-border-radius-base;
				background-color: $uni-color-primary;
			}
			.tip{
				position: absolute;
				z-index: 10;
				top: -8rpx;
				left: 68rpx;
				min-width:20rpx ;
				height: 36rpx;
				background: $uni-color-warning;
				// border-radius: $uni-border-radius-circle;
				border-radius: 18rpx;
				padding: 0 8rpx;
				font-size: $uni-font-size-sm;
				color: $uni-text-color-inverse;
				line-height: 36rpx;
				text-align: center;
			}
			
		}
		.friend-list-r{
			padding-left: 128rpx;
			.top{
				height: 50rpx;
				.name{
					float: left;
					font-size: 36rpx;
					font-weight: 400;
					color: $uni-text-color;
					line-height: 50rpx;
				}
				.time{
					float: right;
					font-size: $uni-font-size-sm;
					color: $uni-text-color-disable;
					line-height: 50rpx;
				}
			}
		}
		.news{
			font-size: $uni-font-size-base;
			color: $uni-text-color-grey;
			line-height: 40rpx;
			display: -webkit-box;
			-webkit-box-orient:vertical;
			-webkit-line-clamp:1;
			overflow: hidden;
		}
	}
</style>
