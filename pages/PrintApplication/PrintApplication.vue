<template>
	<view class="Print-application">
		<view class="Transaction-details-title">
			<loanTitleVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' name='交易流水打印申请' ></loanTitleVue>
		</view>
		<view class="Print-application-ListView">
			<view class="ListView">
				<view class="left">
					姓名
				</view>
				<view class="rigth">
					马文超
				</view>
			</view>
			<view class="ListView">
				<view class="left">
					账户
				</view>
				<view class="rigth">
					6013 ****** 6429
				</view>
			</view>
		</view>
		<view class="Print-application-ListView">
			<view class="ListView">
				<view class="left">
					查询时段
				</view>
				<view class="rigth">
					2024/05/20至2025/05/19 
					<image src="../../static/upsdk_payment_right.webp" mode=""></image>
				</view>
			</view>
		</view>
		<view class="Print-application-box">
			<view class="ListView">
				<view class="left">
					收支
				</view>
				<view class="rigth">
					<view class="btn">全部</view>
					<view class="btn">收入</view>
					<view class="btn">支出</view>
				</view>
			</view>
		</view>
		<view class="Print-application-box">
			<view class="ListView">
				<view class="left">
					币种
				</view>
				<view class="rigth">
					全部 <image src="../../static/upsdk_payment_right.webp" mode=""></image>
				</view>
			</view>
		</view>
		<view class="Print-application-box">
			<view class="ListView">
				<view class="left">
					展示交易对方信息
				</view>
				<view class="rigth">
					<image class="image" src="../../static/application-bg-1.png" mode=""></image>
				</view>
			</view>
		</view>
		<view class="Print-application-box">
			<view class="ListView">
				<view class="left">
					展示完整卡号账户
				</view>
				<view class="rigth">
					<image class="image" src="../../static/application-bg-1.png" mode=""></image>
				</view>
			</view>
		</view>
		<view class="Print-application-ListView">
			<view class="ListView">
				<view class="left">
					是否发送邮箱
				</view>
				<view class="rigth">
					<image class="image" src="../../static/application-bg-1.png" mode=""></image>
				</view>
			</view>
		</view>
		<view class="debtStep-nextStep" @click="dialogToggle('info')">
			申请
		</view>
		
								
		<uni-popup ref="alertDialog" type="dialog">
			<uni-popup-dialog :type="msgType" :showClose='false' cancelText="关闭"  content="您选择的时间跨度内暂无交易流水，建议您选择更大的时间跨度或更换币种、收支" @close="dialogClose"></uni-popup-dialog>
		</uni-popup>
	</view>
</template>

<script>
	import loanTitleVue from '../../components/loan-Title.vue';
	export default {
		data() {
			return {
				TitleImage:"../../static/back_black.png",
				rigthIcon:['../../static/boc_folder_title_service.png'],
				type: 'center',
				msgType: 'success',
			};
		},
		components:{
			loanTitleVue
		},
		methods:{
			dialogToggle(type) {
				this.msgType = type
				this.$refs.alertDialog.open()
			},
			dialogClose(){
				this.$refs.alertDialog.close()
			}
		}
	}
</script>

<style lang="scss">
	.Print-application{
		width: 100vw;
		height: 100vh;
		background: #f4f4f4;
		.Transaction-details-title{
			background-color: #fff;
			font-weight: bold;
		}
		.Print-application-ListView{
			width: 95%;
			margin: 0 auto;
			background-color: #fff;
			margin-top: 20rpx;
			font-size: 35rpx;
			border-radius: 10rpx;
			.ListView{
				padding: 30rpx;
				display: flex;
				justify-content: space-between;
				align-items: center;
				border-bottom: 1px solid #f7f7f7;
				.left{
					font-weight: bold;
				}
				.rigth{
					text-align: right;
					display: flex;
					align-items: center;
					image{
						width: 50rpx;
						height: 50rpx;
					}
					.image{
						width: 120rpx;
						height: 75rpx;
					}
				}
			}
		}
		.Print-application-box{
			width: 95%;
			margin: 0 auto;
			background-color: #fff;
			font-size: 35rpx;
			border-radius: 10rpx;
			.ListView{
				padding: 30rpx;
				display: flex;
				justify-content: space-between;
				align-items: center;
				border-bottom: 1px solid #f7f7f7;
				.left{
					font-weight: bold;
				}
				.rigth{
					display: flex;
					text-align: right;
					align-items: center;
					image{
						width: 50rpx;
						height: 50rpx;
					}
					.btn{
						padding: 10rpx 25rpx;
						border: 1px solid #ac717e;
						border-radius: 10rpx;
						font-size: 30rpx;
						margin-left: 20rpx;
						font-weight: bold;
						background-color: #f4f4f4;
					}
					.btn:hover{
						background-color: #feeaeb;
						color: #d2304c;
					}
					.image{
						width: 120rpx;
						height: 75rpx;
					}
				}
			}
		}
		.debtStep-nextStep{
			display: flex;
			align-items: center;
			width: 90%;
			margin: 0 auto;
			margin-top: 50rpx;
			color: #fff;
			justify-content: center;
			padding: 20rpx 0;
			border-radius: 10rpx;
			background:linear-gradient(to right , #72b6fd ,#3e93ea) ;
		}
	}
</style>
