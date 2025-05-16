<template>
	<view class="index-title">
		
		<view class="login" @click="Gologin">
			<image src="@/static/boc_folder_title_login_pre.png" mode=""></image>
			<p>登录</p>
		</view>
		<view class="title-input">
			<image src="@/static/boc_finance_search.png" mode=""></image>
			<input type="text" placeholder="请输入" />
			<image src="@/static/boc_finance_search.png" mode=""></image>
		</view>
		<view class="title-icon">
			<image src="@/static/boc_folder_title_login_next.png" mode=""></image>
			<p>版本</p>
		</view>
		<view class="title-icon">
			<image src="@/static/boc_folder_title_service.png" mode=""></image>
			<p>客服</p>
		</view>
		<view class="title-icon">
			<image src="@/static/boc_folder_title_msg.png" mode=""></image>
			<p>消息</p>
		</view>
	</view>
</template>

<script>
	export default {
		name:"SeachTitle",
		data() {
			return {
				
			};
		},
		components:{
			
		},
		methods:{
			Gologin(){
				uni.navigateTo({
					url:'/pages/login/login'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.index-title{
		display: flex;
		align-items: center;
		justify-content: space-between;
		font-size: 28rpx;
		background-color: #fff;
		padding:0 30rpx;
		p{
			text-align: center;
			width: 100%;
			margin-top: 5rpx;
		}
		.login{
			color: #000;
			display: flex;
			flex-wrap: wrap;
			justify-content: center;
			margin-right: 20rpx;
			image{
				width: 40rpx;
				height: 40rpx;
			}
		}
		.title-input{
			width: 300rpx;
			height: 70rpx;
			border-radius: 50rpx;
			background-color: #f4f4f4;
			display: flex;
			align-items: center;
			justify-content: center;
			padding:0 20rpx;
			image{
				width: 35rpx;
				height: 35rpx;
			}
			input{
				flex: 1;
				font-size: 28rpx;
				margin: 0 20rpx;
			}
		}
		.title-icon{
			color: #000;
			display: flex;
			flex-wrap: wrap;
			justify-content: center;
			margin-left: 20rpx;
			image{
				width: 40rpx;
				height: 40rpx;
			}
			p{
				text-align: center;
				width: 100%;
			}
		}
	}
</style>