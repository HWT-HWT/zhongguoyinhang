<template>
	<view class="AccountTransfer">
		<view class="transfer-topTitle">
			<loanTitleVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' name="账号转账"  ></loanTitleVue>
		</view>
		<view class="repayment-Account">
			<p>交易账户</p>
			<view class="image-text">
				6216 ****** 6429 
				<image src="../../static/upsdk_payment_right.webp" mode=""></image> 
			</view>
		</view>
		<view class="AccountTransfer-money">可用余额: <text>人民币元 45,084.39</text></view>
		<view class="repayment-Type">
			<p>币种</p>
			<view class="image-text">
				人民币元
			</view>
		</view>
		<view class="AccountTransfer-Number">
			<p>转账金额</p>
			<input type="text" placeholder="请输入"/>
		</view>
		<view class="AccountTransfer-ListView">
			<view class="AccountTransfer-list">
				<p>收款人名称</p>
				<input type="text" placeholder="请输入" />
				<view class="icon">
					<image src="@/static/AccountTransfer-icon-1.png" mode=""></image>
					<p>收款人</p>
				</view>
			</view>
			<view class="AccountTransfer-list" style="border: none;">
				<p>收款账户</p>
				<input type="text" placeholder="请输入" />
				<view class="icon">
					<image src="@/static/AccountTransfer-icon-2.png" mode=""></image>
					<p>拍照</p>
				</view>
			</view>
		</view>
		<view class="AccountTransfer-ListView">
			<view class="AccountTransfer-list">
				<p>附言</p>
				<input type="text" placeholder="非必输" />
				<view class="icon">
					
				</view>
			</view>
			<view class="AccountTransfer-list" style="border: none;">
				<p>预约执行</p>
				<text></text>
				<view class="icon" style="width: 15%;">
					<image style="width: 100%; height: 60rpx;" src="@/static/application-bg-2.png" mode=""></image>
				</view>
			</view>
		</view>
		<view class="AccountTransfer-btn">
			下一步
		</view>
		<view class="AccountTransfer-footer">
			1.为了您的资金安全，请注意核实收款人身份，不要轻信陌生人通过网络、电话、短信等方式告知的信息，谨防电信网络诈骗。<span>查看详情</span>
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
		.AccountTransfer-money{
			padding: 20rpx;
			font-size: 25rpx;
			text{
				color: #8a0000;
				font-weight: bold;
			}
		}
		.repayment-Type{
			width: 90%;
			margin: 0 auto;
			background-color: #fff;
			display: flex;
			align-items: center;
			justify-content: space-between;
			padding: 25rpx;
			border-bottom: 1px solid #ddd;
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
		.AccountTransfer-Number{
			width: 90%;
			padding: 25rpx;
			margin: 0 auto;
			background-color: #fff;
			p{
				font-size: 32rpx;
				font-weight: bold;
			}
			input{
				margin-top: 20rpx;
				font-size: 40rpx
			}
		}
		.AccountTransfer-ListView{
			margin-top: 20rpx;
			.AccountTransfer-list{
				width: 90%;
				margin: 0 auto;
				padding:20rpx 25rpx;
				background-color: #fff;
				border-bottom: 1px solid #ddd;
				display: flex;
				justify-content: space-between;
				align-items: center;
				p{
					width: 25%;
					font-size: 32rpx;
					font-weight: bold;
				}
				input{
					font-size: 32rpx;
					margin-right: 50rpx;
				}
				.icon{
					width: 50rpx;
					display: flex;
					flex-wrap: wrap;
					align-items: center;
					justify-content: center;
					image{
						width: 40rpx;
						height: 40rpx;
					}
					p{
						display: flex;
						justify-content: center;
						width: 100%;
						margin-top: 5rpx;
						font-size: 15rpx;
						font-weight: normal;
						color: #2c70ef;
					}
				}
			}
		}
		.AccountTransfer-btn{
			width: 90%;
			display: flex;
			align-items: center;
			justify-content: center;
			margin: 0 auto;
			margin-top:80rpx;
			padding:20rpx 25rpx;
			border-radius: 10rpx;
			background-color: #2c70ed;
			font-weight: bold;
			color: #fff;
		}
		.AccountTransfer-footer{
			width: 90%;
			padding: 25rpx;
			font-size: 25rpx;
			color: #6b6b6b;
			span{
				color: #2c70ed;
				font-weight: bold;
			}
		}
	}
</style>
