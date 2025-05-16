<template>
	<view class="login">
		<view class="login-back">
			<occupyVue hight="90rpx"></occupyVue>
			<image class="left" src="@/static/upsdk_payment_right.webp" mode="" @click="Back"></image>
			<image src="@/static/boc_folder_title_service.png" mode=""></image>
		</view>
		<view class="login-Title">
			你好,<br>
			欢迎来到中国银行
		</view>
		<view class="login-input">
			<view class="input-box">
				<p>+86</p>
				<input type="tel" placeholder="手机号(中国内地)"  placeholder-style="color:#888; font-size:35rpx" v-model="Phone" maxlength="11"/>
			</view>
		</view>
		<view class="login-checkbox">
			<label>
				<checkbox iconColor="#fff" activeBackgroundColor='#ce0000' borderColor='#ce0000' activeBorderColor='#ce0000' />
			</label>
			<text>我已同意<text>《中国银行股份有限公司手机银行服务协议》、《中国银行股份有限公司手机银行隐私服务政策》。</text></text>
		</view>
		<view class="login-botton" @click="initLogin">
			下一步
		</view>
		<view class="login-language">
			<span>查余额</span>
			<span style="border: none;">语言/Language</span>
		</view>
		<view class="login-wechat">
			<image src="@/static/login_manage_authorization_wx.png" mode=""></image>
		</view>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue';
	
	export default {
		data() {
			return {
				Phone:''
			};
		},
		components:{
			occupyVue,
		},
		methods:{
			Back(){
				uni.navigateBack()
			},
			initLogin(){
				if(this.Phone){
					uni.setStorageSync('account',{token:this.Phone})
					uni.reLaunch({
						url:'/pages/index/index'
					})
				}else{
					uni.showToast({
						title:'请输入手机号/勾选下方协议',
						icon:'none'
					})
				}
				
			},
			gestureChange(points){
				console.log(points)
			},
		}
	}
</script>

<style lang="scss">
	.login{
		width: 100vw;
		height: 100vh;
		background:url('@/static/boc_login_background.png')no-repeat;
		background-size: 350rpx 500rpx;
		background-position: right top;
		.login-back{
			display: flex;
			flex-wrap: wrap;
			align-items: center;
			justify-content: space-between;
			padding: 30rpx;
			.left{
				transform: scale(-1);
				width: 60rpx;
				height: 60rpx;
			}
			image{
				width: 40rpx;
				height: 40rpx;
				padding:0 10rpx;
				padding-top:10rpx;
			}
		}
		.login-Title{
			font-size: 50rpx;
			display: flex;
			padding:100rpx 50rpx;
			font-weight: bold;
		}
		.login-input{
			width: 90%;
			margin: 0 auto;
			padding-bottom: 20rpx;
			border-bottom: 1rpx solid #e6e6e6;
			padding-top: 120rpx;
			.input-box{
				width: 100%;
				display: flex;
				align-items: center;
				p{
					margin: 0 20rpx;
				}
				input{
					margin-left: 10rpx;
					color: #666;
					font-size: 35rpx;
				}
			}
		}
		.login-checkbox{
			width: 90%;
			margin: 0 auto;
			margin-top: 40rpx;
			font-size: 28rpx;
			display: flex;
			flex-wrap: nowrap;
			justify-content: center;
			checkbox{
				transform: scale(0.6);
				
			}
			text{
				width: 100%;
				// letter-spacing: 1rpx;
				line-height: 45rpx;
				margin-left: 10rpx;
				text{
					color: #2d84ec;
					
				}
			}
		}
		.login-botton{
			width: 90%;
			margin: 0 auto;
			background-color: #ce0000;
			text-align: center;
			margin-top: 40rpx;
			color: #fff;
			padding: 20rpx 0;
			border-radius: 50rpx;
			font-size: 35rpx
		}
		.login-language{
			width: 90%;
			display: flex;
			align-items: center;
			justify-content: center;
			margin: 20rpx auto;
			span{
				color: #555;
				border-right: 1px solid #ccc;
				padding-right: 30rpx;
				margin: 20rpx;
				font-size: 28rpx
			}
		}
		.login-wechat{
			position: absolute;
			bottom: 3%;
			left: 45%;
			image{
				width: 60rpx;
				height: 60rpx;
			}
		}
	
	}
</style>
