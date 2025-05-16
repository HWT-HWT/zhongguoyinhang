<template>
	<view class="repayment">
		<view class="repayment-title">
			<loanTitleVue name="提前还款申请" :TitleImage='TitleImage' :rigthIcon='rigthIcon'></loanTitleVue>
		</view>
		<view class="repayment-prompt">
			<image src="@/static/boc_marquee_hint.png" mode=""></image> <p>该申请需要审批,最终结果一审批为准,请注意查收审批结果短信</p>
		</view>
		<view class="repayment-ListView">
			<view class="repayment-View">
				<p>贷款名称</p>
				<view class="image-text">
					个人经营贷款 
				</view>
			</view>
			<view class="repayment-View">
				<p>还款总额</p>
				<view class="image-text">
					人民币元 458,600.00 
				</view>
			</view>
		</view>
		<view class="repayment-input">
			<view class="input-title">
				<p>提前还款本金金额(人民币元)</p>
				<span>全额还款</span>
			</view>
			<input type="text" placeholder="最小金额1,000.00" placeholder-style="fontSize:40rpx" maxlength="10"/>
			<p class="p">后续还款安排</p>
		</view>
		<view class="repayment-nextStep">
			下一步
		</view>
		<view class="repayment-remind">
			温馨提示: <br />
			1、提前还款可以能会产生违约金,根据金额以您的贷款合同为准<br />
			2、系统服务时间为北京时间每日7:00-22:00,请您在此期间办理主动还款<br />
			3、如有问题,联系贷款经办网点或 <span>95566</span>
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
		},
		methods:{
			
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
		.repayment-prompt{
			width: 95%;
			margin: 0 auto;
			font-size: 30rpx;
			background-color: #fbf8f1;
			display: flex;
			align-items: center;
			image{
				width: 45rpx;
				height: 35rpx;
				margin-left: 20rpx;
			}
			p{
				color: #000;
				padding: 20rpx;
			}
		}
		.repayment-ListView{
			margin-top: 20rpx;
			.repayment-View{
				width: 90%;
				background-color: #fff;
				margin: 0 auto;
				margin-top: 5rpx;
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
		}
		.repayment-input{
			width: 97%;
			margin: 0 auto;
			margin-top: 20rpx;
			background-color: #fff;
			.input-title{
				padding: 20rpx;
				display: flex;
				align-items: center;
				justify-content: space-between;
				p{
					font-size: 30rpx;
					font-weight: bold;
				}
				span{
					color: #1170f0;
					font-size: 28rpx;
				}
			}
			input{
				padding: 20rpx;
				font-size: 40rpx;
				border-bottom: 1px solid #f4f4f4;
			}
			.p{
				font-size: 30rpx;
				padding: 20rpx;
				font-weight: bold;
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
			span{
				color: #1170f0;
			}
		}
	}
</style>
