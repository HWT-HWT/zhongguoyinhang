<template>
	<view class="AccountTransfer">
		<view class="transfer-topTitle">
			<loanTitleVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' name="转账汇款"  ></loanTitleVue>
		</view>
		<view class="repayment-Account">
			<p>交易账户</p>
			<view class="image-text">
				6216 ****** 6429 
				<image src="../../static/upsdk_payment_right.webp" mode=""></image> 
			</view>
		</view>
	</view>
</template>

<script>
	import loanTitleVue from '../../components/loan-Title.vue';
	export default {
		data() {
			return {
				TitleImage:"../../static/back_black.png",
				rigthIcon:['../../static/boc_folder_title_service.png','../../static/icon_share_black.png'],
			};
		},
		components:{
			loanTitleVue
		}
	}
</script>

<style lang="scss" scoped>
	.AccountTransfer{
		width: 100vw;
		height: 100vh;
		background-color: #f4f4f4;
		.transfer-topTitle{
			background-color: #fff;
		}
		.repayment-Account{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			background-color: #fff;
			display: flex;
			align-items: center;
			justify-content: space-between;
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
	}
</style>
