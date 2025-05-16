<template>
	<view class="overdue">
		
		<!-- <view class="overdue-box">
			<view class="overdue-Datali">
				<view class="Row">
					<view class="p"> 逾期期数 </view>
					<span class="none">6期</span>
				</view>
				<view class="Row">
					<view class="p">应还总额</view>
					<span>41,705.57</span>
				</view>
			</view>
			<view class="overdue-text">
				本金10,800.00 | 利息30,905.57
			</view>
			<view class="repayment-nextStep" @click="Eext">
				下一步
			</view>
		</view> -->
		
		<image src="@/static/current_have_nothing.png" mode=""></image>
		<p>无逾期还款记录</p>
	</view>
</template>

<script>
	export default {
		name:"overdue",
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss" scoped>
	.overdue{
		width: 100vw;
		// .overdue-box{
		// 	width: 90%;
		// 	margin: 0 auto;
		// 	background-color: #fff;
		// 	padding-bottom: 10rpx;
		// 	border-radius: 10rpx;
		// 	.overdue-Datali{
		// 		width: 100%;
		// 		margin: 0 auto;
		// 		color: #000;
		// 		display: flex;
		// 		margin-top: 20rpx;
		// 		.Row{
		// 			margin-top: 20rpx;
		// 			text-align: center;
		// 			flex-wrap: wrap;
		// 			width: 50%;
		// 			line-height: 60rpx;
		// 			justify-content: center;
		// 			.p{
		// 				color: #888;
		// 				font-size: 28rpx;
		// 				image{
		// 					width: 40rpx;
		// 					height: 40rpx;
		// 				}
		// 			}
		// 			span{
		// 				font-size: 35rpx;
		// 				font-weight: bold;
		// 				color: #000;
		// 			}
		// 			.none{
		// 				color: #e75f72;
		// 			}
		// 		}
		// 	}
		// 	.overdue-text{
		// 		text-align: center;
		// 		font-size: 25rpx;
		// 		color: #888;
		// 		padding: 30rpx;
		// 	}
		// 	.repayment-nextStep{
		// 		display: flex;
		// 		align-items: center;
		// 		width: 90%;
		// 		background-color: blue;
		// 		margin: 30rpx auto;
		// 		color: #fff;
		// 		justify-content: center;
		// 		padding: 20rpx 0;
		// 		border-radius: 10rpx;
		// 		font-weight: bold;
		// 	}
		// }
		
		display: flex;
		align-items: center;
		justify-content: center;
		margin-top: 400rpx;
		flex-wrap: wrap;
		image{
			width: 300rpx;
			height: 300rpx;
		}
		p{
			width: 100%;
			text-align: center;
			color: #666;
			font-size: 30rpx;
			margin-top: 20rpx;
		}
	}
</style>