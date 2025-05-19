<template>
	<view class="repayment">
		<view class="repayment-title">
			<loanTitleVue name="提前还款" :TitleImage='TitleImage' :rigthIcon='rigthIcon'></loanTitleVue>
		</view>
		<view class="repayment-View">
			<p>用款记录</p>
			<view class="image-text">
				请选择 
				<image src="../../static/upsdk_payment_right.webp" mode=""></image> 
			</view>
		</view>
		<view class="repayment-Account">
			<p>还款账户</p>
			<view class="image-text">
				6216 ****** 6429
				<image src="../../static/upsdk_payment_right.webp" mode=""></image> 
			</view>
		</view>
		<view class="repayment-balance">
			可用余额: <span>人民币元 0.00</span>
		</view>
		<view class="repayment-nextStep">
			下一步
		</view>
		<view class="repayment-remind">
			系统服务时间为北京时间每日7:00-22:00,请您在此期间办理主动还款
		</view>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue';
	import loanTitleVue from '../../components/loan-Title.vue';
	export default {
		data() {
			return {
				TitleImage:"../../static/back_black.png",
				rigthIcon:['../../static/boc_folder_title_service.png'],
			};
		},
		components:{
			occupyVue,
			loanTitleVue
		}
	}
</script>

<style lang="scss" scoped>
	.repayment{
		width: 100vw;
		height: 100vh;
		background-color: #f7f7f7;
		.repayment-title{
			background-color: #fff;
			padding-bottom: 20rpx;
		}
		.repayment-View{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			background-color: #fff;
			display: flex;
			align-items: center;
			justify-content: space-between;
			border-radius: 10rpx;
			padding: 25rpx;
			p{
				font-weight: bold;
			}
			.image-text{
				display: flex;
				align-items: center;
				color: #666;
				image{
					width: 50rpx;
					height: 50rpx;
				}
			}
			
		}
		.repayment-Account{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			background-color: #fff;
			display: flex;
			align-items: center;
			justify-content: space-between;
			border-radius: 10rpx;
			padding: 25rpx;
			p{
				font-weight: bold;
			}
			.image-text{
				display: flex;
				align-items: center;
				image{
					width: 50rpx;
					height: 50rpx;
				}
			}
			
		}
		.repayment-balance{
			width: 90%;
			margin: 0 auto;
			font-size: 28rpx;
			padding: 30rpx;
			color: #666;
			span{
				color: #8a0000;
			}
		}
		.repayment-nextStep{
			display: flex;
			align-items: center;
			width: 90%;
			background-color: blue;
			margin: 30rpx auto;
			color: #fff;
			justify-content: center;
			padding: 20rpx 0;
			border-radius: 10rpx;
			font-weight: bold;
		}
		.repayment-remind{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			font-size: 28rpx;
			color: #666;
			font-weight: bold;
		}
	}
</style>
