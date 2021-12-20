<template>
	<view class="content">
		<view class="top-bar" @tap="tosignin">
			<view class="top-bar-left">
				<image class="back-img" src="../../static/images/common/back.png" mode=""></image>
			</view>
		</view>
		<view class="logo">
			<image src="" ></image>
		</view>
		<view class="main">
			<view class="title">
				注册
			</view>
			<view class="inputs">
				<view class="inputs-div">
					<input type="text" value="" placeholder="请取个名字"  class="user"  @input="getUser" placeholder-style="color:#aaa;font-weight:400;" />
					<view class="employ" v-if="employ">
						已占用
					</view>
					<image src="../../static/images/sign/right1.png" class="ok" mode="" v-if="isuser"></image>
				</view>
				
				<view class="inputs-div">
					<input type="text"  v-model = "email" value="" placeholder="请输入邮箱"  class="email"  placeholder-style="color:#aaa;font-weight:400;" 
					@input="isEmail"
					/>
					<view class="employ" v-if="employ">
						已占用
					</view>
					<view class="invalid" v-if="invalid" >
						邮箱无效
					</view>
					<image src="../../static/images/sign/right1.png" class="ok" v-if="isemail" mode=""></image>
				</view>
				
				
				
				
				<view class="inputs-div">
					<input :type="type" value="" placeholder="这里输入密码"   @input="getPsw"  class="psw" placeholder-style="color:#aaa;font-weight:400;" />
				<!-- 	<view class="employ" v-if="employ">
						已占用
					</view> -->
					<image :src="lookurl" class="look" mode="" @tap="looks"></image>
					
				</view>
				
			</view>
			
		</view>
		<view :class="[{submit:isok},{submit1:!isok}]">
			注册
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				type:"password",
				isuser:true, //用户名是否占用
				isemail:false, // 邮箱是否占用
				look:false, //是否显示密码
				invalid:false,//邮箱是否无效
				employ:false,//是否被占用
				lookurl:"../../static/images/sign/biyan.png",
				email:'', //邮箱
				isok:false ,//注册按钮灰色控制
				
				user:'',
				psw:'',
			}
		},
		methods: {
			//密码显示方法
			looks:function(){
				if(this.look){
					this.type="password";
					this.look=!this.look;
					this.lookurl = "../../static/images/sign/biyan.png";
				}else{
					this.type="text";
					this.look=!this.look
					this.lookurl= "../../static/images/sign/look.png";
				}
			},
			//判断是否为邮箱格式
			isEmail:function(e){
				
				let reg = /^([a-zA-Z]|[0-9])(\w|\-)+@[a-zA-Z0-9]+\.([a-zA-Z]{2,4})$/;
				if(this.email.length>0){
					if( reg.test(this.email)){
						console.log("正确")
						this.invalid  = false
						this.isemail = true
					}else{
						console.log("不正确")
						this.invalid  = true
						this.isemail = false
					}
				}else{
					this.invalid  = false
					//this.isemail = true
				}
			},
			//跳转到signin
			tosignin: function(){
				uni.navigateBack({
					delta:1
				})
			},
			//判断是否可以注册了
			isOk:function(){
				if(this.isuser && this.isemail && this.psw.length > 5 ){
					this.isok = true;
				}
			},
			
			getUser:function(e){
				//console.log(e)
				this.user = e.detail.value
				console.log(this.user)
				this.isOk();
			},
			getPsw:function(e){
				//console.log(e)
				this.psw = e.detail.value
				console.log(this.psw)
				this.isOk();
			},
			getEmail:function(e){
				//console.log(e)
				this.email = e.detail.value
				this.isOk();
			},
		}
	}
</script>

<style lang="scss">
	@import "../../commons/css/mycss.scss";
.top-bar{
		background: $uni-bg-color;
		.top-bar-left{
			padding-left: 32rpx;
			//background-color: #eee;
			width: 88rpx;
			height: 88rpx;
		}
	}
.logo {
	text-align: center;
	image{
		padding-top: 256rpx;
		width: 194rpx;
		height: 92rpx;
		margin: 0auto;
	}
}
.main{
	padding: 54rpx $uni-spacing-row-lg 120rpx;
	//width: 100%;
	.title{
		font-size: 56rpx;
		font-weight: 500;
		color:$uni-text-color;
		line-height: 80rpx;
	}
	.slogan{
		font-size: 40rpx;
		color: rgba(39,40,50,0.5);
		line-height: 56rpx;
	}
	.inputs{
		padding-top: 8rpx;
		input{
			padding-top: 40rpx;
			height: 88rpx;
			font-size: $uni-font-size-lg;
			font-weight: 500;
			color: $uni-text-color;
			line-height: 88rpx;
			border-bottom: 1px solid $uni-border-color;
		}
		
	}
	.inputs-div{
		position: relative;
		
	}
	.employ ,.invalid{
		position: absolute;
		right: 0;
		top: 40rpx;
		font-size: $uni-font-size-base;
		font-weight: 500;
		color: $uni-color-warning;
		line-height: 88rpx;
	}
	.ok{
		position: absolute;
		right: 0;
		top: 76rpx;
		width: 38rpx;
		height: 30rpx;
	}
	.look{
		position: absolute;
		right: 0;
		top: 76rpx;
		width: 32rpx;
		height: 18rpx;
	}
	
}

.submit{
	margin:  0 auto;
	width: 520rpx;
	height: 96rpx;
	background: $uni-color-primary;
	box-shadow: 0px 50rpx 32rpx -36rpx rgba(255,228,49,0.4);
	border-radius:48rpx;
	font-size:  $uni-font-size-lg;
	font-weight: 500;
	color:$uni-text-color;
	line-height: 96rpx;
	text-align:center ;
	
}
.submit1{
	margin:  0 auto;
	width: 520rpx;
	height: 96rpx;
	background: rgba(39,48,50,0.2);
	border-radius:48rpx;
	font-size:  $uni-font-size-lg;
	font-weight: 500;
	color:$uni-text-color-inverse;
	line-height: 96rpx;
	text-align:center ;
	
}
</style>
