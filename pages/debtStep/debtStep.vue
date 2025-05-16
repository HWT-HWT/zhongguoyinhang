<template>
	<view class="debtStep">
		<view class="debtStep-title">
			<loanTitleVue name="还款" :TitleImage='TitleImage' :rigthIcon='rigthIcon'></loanTitleVue>
		</view>
		<view class="debtStep-View">
			<view class="assets-Datali">
				<view class="Row">
					<view class="p">本期应还(元) </view>
					<span class="none">3,047.12</span>
				</view>
				<view class="Row" style="border: none;">
					<view class="p">贷款余额(元) </view>
					<span  class="none">458,600.00</span>
				</view>
			</view>
<!-- 			<view class="prompt">
				<view class="prompt-Text">
					<p>您当前存在欠款，请尽快还款。</p>
					<p>逾期总额: <span>人民币元 41.705.57</span> </p>
				</view>
			</view> -->
			<view class="Loan-Datali-ListView">
				<view class="ListView" v-for="(item,index) in LoanDataliList " :key="index">
					<view class="name">
						{{item.name}}
					</view>
					<view class="text">
						{{item.text}}
					</view>
					<view class="menu" v-if="item.menu">
						{{item.menu}}
					</view>
				</view>
			</view>
		</view>
		<view class="debtStep-nextStep" @click="Next()">
			提前还款申请
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
				LoanDataliList:[
					{name:'贷款名称',text:'个人经营贷款'},
					{name:'本期还款日',text:'2025/04/03'},
					{name:'还款账户',text:'6216 ****** 919O'},
					{name:'还款方式',text:'协议还款'},
				],
			};
		},
		components:{
			loanTitleVue
		},
		methods:{
			Next(){
				uni.navigateTo({
					url:'/pages/debt/debt'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.debtStep{
		width: 100%;
		height: 100vh;
		background:#f4f4f4;
		.debtStep-title{
			background-color: #fff;
		}
		.debtStep-View{
			width: 90%;
			margin: 0 auto;
			border-radius: 20rpx;
			background-color: #fff;
			.assets-Datali{
				width: 100%;
				margin: 0 auto;
				color: #000;
				display: flex;
				margin-top: 20rpx;
				.Row{
					width: 50%;
					text-align: center;
					padding: 20rpx;
					line-height: 55rpx;
					.p{
						text-align: center;
						color: #888;
						font-size: 30rpx;
					}
					span{
						text-align: center;
						font-size: 40rpx;
						font-weight: bold;
						color: #000;
					}
				}
			}
			.prompt{
				width: 90%;
				margin: 0 auto;
				background-color: #f4f4f4;
				border-radius: 10rpx;
				margin-bottom: 20rpx;
				.prompt-Text{
					padding: 30rpx;
					p{
						font-size: 25rpx;
						span{
							color: #800000;
							font-weight: bold;
						}
					}
				}
			}
			.Loan-Datali-ListView{
				border-top:1px solid #ddd ;
				width: 100%;
				background-color: #fff;
				padding-bottom: 20rpx;
				.ListView{
					display: flex;
					font-size: 28rpx;
					padding: 20rpx;
					margin-top: 10rpx;
					.name{
						width: 30%;
					}
					.text{
						flex: 1;
						font-size: 28rpx;
						font-weight: bold;
					}
					.menu{
						width: 10%;
						color: #1170f0;
					}
				}
			}
		}
		.debtStep-nextStep{
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
	}
</style>
