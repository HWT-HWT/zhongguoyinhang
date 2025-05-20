<template>
	<view class="drawMoney">
		<view class="drawMoney-tbas">
			<loanTitleVue name="中银E贷·经营贷" :TitleImage='TitleImage' :rigthIcon='rigthIcon'></loanTitleVue>
		</view>
		<view class="drawMoney-Title-text">
			<view class="drawMoney-title">
				惠如愿·E抵贷
			</view>
			<view class="drawMoney-Number">
				贷款额度号 PF446330000020201608283
			</view>
		</view>
		<view class="drawMoney-ListView">
			<view class="ListView-text">
				<p>可用额度(元)</p>
				<view class="money">0.00</view>
				<view class="date">2034/10/25到期 年化利率3.36%起 <image src="@/static/boc_finance_gray_help.png" mode=""></image> </view>
			</view>
			<view class="ListView-btn">
				<!-- <span>用款</span> -->
				<span style="border: none;" @click="Next()">更多</span>
			</view>
		</view>
		<view class="drawMoney-bill">
			待还款,共1笔
		</view>
		<view class="drawMoney-List">
			<view class="List-title">
				<span>2024/06/24</span>
				<span class="money">用款 600,000.00</span>
			</view>
			<view class="assets-Datali">
				<view class="Row">
					<view class="p">还款日</view>
					<span class="none">2025/04/03</span>
				</view>
				<view class="Row" style="border: none;">
					<view class="p">应还</view>
					<span  class="none">6,259.82</span>
				</view>
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
				rigthIcon:['../../static/boc_folder_title_service.png'],
			};
		},
		components:{
			loanTitleVue
		},
		methods:{
			Next(){
				uni.navigateTo({
					url:'/pages/more/more'
				})
			}
		}
	}
</script>

<style lang="scss">
	.drawMoney{
		width: 100vw;
		height: 100vh;
		background: #f7f7f7;
		.drawMoney-tbas{
			background-color: #fff;
			padding-bottom: 20rpx;
			font-weight: bold;
		}
		.drawMoney-Title-text{
			width: 95%;
			margin: 0 auto;
			margin-top: 20rpx;
			.drawMoney-title{
				font-size: 32rpx;
				font-weight: bold;
				padding-left: 20rpx;
				border-left: 10rpx solid #daa969;
			}
			.drawMoney-Number{
				font-size: 28rpx;
				color: #888;
				margin-top: 10rpx;
				text-align: right;
			}
		}
		.drawMoney-ListView{
			width: 95%;
			margin: 0 auto;
			border-radius: 20rpx;
			margin-top: 20rpx;
			background-color: #fff;
			padding: 20rpx 0;
			.ListView-text{
				display: flex;
				align-items: center;
				flex-wrap: wrap;
				justify-content: center;
				border-bottom:1px solid #ddd ;
				padding-bottom: 20rpx;
				p{
					font-size: 32rpx;
				}
				.money{
					text-align: center;
					width: 100%;
					font-size: 60rpx;
					font-weight: bold;
					margin: 20rpx auto;
					color: #daa969;
				}
				.date{
					font-size: 32rpx;
					display: flex;
					align-items: center;
					image{
						width: 30rpx;
						height: 30rpx;
						margin-left: 10rpx;
					}
				}
			}
			.ListView-btn{
				display: flex;
				justify-content: center;
				align-items: center;
				margin-top: 20rpx;
				span{
					width: 50%;
					border-right: 1px solid #ddd;
					text-align: center;
					font-size: 30rpx;
					font-weight: bold;
					color: #daa969;
				}
			}
		}
		.drawMoney-bill{
			width: 95%;
			margin: 0 auto;
			font-size: 32rpx;
			margin-top: 20rpx;
		}
		.drawMoney-List{
			width: 95%;
			margin: 0 auto;
			background-color: #fff;
			border-radius: 20rpx;
			padding-bottom: 20rpx;
			margin-top: 20rpx;
			.List-title{
				background-color: #f4f4f4;
				padding:10rpx;
				font-size: 30rpx;
				display: flex;
				align-items: center;
				.money{
					margin-left: 70rpx;
				}
			}
			.assets-Datali{
				width: 100%;
				margin: 0 auto;
				color: #000;
				display: flex;
				margin-top: 20rpx;
				.Row{
					display: flex;
					align-items: center;
					border-right: 1px solid #ddd;
					flex-wrap: wrap;
					width: 50%;
					line-height:40rpx;
					padding-left: 50rpx;
					justify-content: center;
					.p{
						display: flex;
						align-items: center;
						justify-content: center;
						color: #888;
						width: 100%;
						font-size: 28rpx;
					}
					span{
						font-size: 30rpx;
					}
					.none{
						font-size: 35rpx;
						color: #000;
						margin-top: 10rpx;
						font-weight: bold;
					}
				}
			}
		}
	}
</style>
