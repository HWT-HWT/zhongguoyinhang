<template>
	<view class="drawMoney">
		<view class="drawMoney-tbas">
			<loanTitleVue name="随心智贷" :TitleImage='TitleImage' :rigthIcon='rigthIcon' :Scollor="scrollTop"></loanTitleVue>
		</view>
		<view class="drawMoney-ListView">
			<view class="ListView-text">
				<p>可用额度(元)</p>
				<view class="money">0.<span>00</span> </view>
				<view class="date">年利率(单利)3.4% <image src="@/static/boc_finance_gray_help.png" mode=""></image> | 2027/11/08到期 </view>
			</view>
		</view>
		
		
		<swiper :indicator-dots="true" :autoplay="false" :interval="3000" :duration="1000">
			<swiper-item>
				<view class="FeelFreeLoan-ListView">
					<ListView :listTitle='FeelFreeLoanlist' :Pad="'30rpx 0'" FontSize="20rpx" sizi='50rpx' @ClickNext='GoNext'></ListView>
				</view>
			</swiper-item>
			<swiper-item>
				<view class="FeelFreeLoan-ListView">
					<ListView :listTitle='FeelFreeLoanlistTow' :Pad="'30rpx 0'" FontSize="20rpx" sizi='50rpx'></ListView>
				</view>
			</swiper-item>
		</swiper>
		
		<view class="drawMoney-guangao">
			<image src="../../static/FeelFreeLoan-bg-1.png" mode=""></image>
			<view class="guangao">
				<p>分享功能给好友</p> 
				<view>随心智贷 最高可借50w <image src="@/static/upsdk_mp_help.webp" mode=""></image> </view>
			</view>
			<view class="btn" >
				去邀请
			</view>
		</view>
		
		<view class="drawMoney-guangao" style="background-color: #f3faff;">
			<image src="../../static/FeelFreeLoan-bg-2.png" mode=""></image>
			<view class="guangao">
				<p>获取有惊喜</p> 
				<view>贷款热门活动</view>
			</view>
			<view class="btn" style="border:1px solid #61a1f5;color: #1572f0;">
				去看看
			</view>
		</view>
		
		<view class="drawMoney-List">
			<view class="List-title">
				<span>待还款,共1笔</span>
				<span class="money">单位:人民币</span>
			</view>
			<view class="assets-Datali" @click="Next">
				<view class="Row">
					<view class="p">2024/11/13用款</view>
					<span class="none">200,000.00</span>
				</view>
				<view class="Row" style="border: none;">
					<view class="p">2025/06/11应还</view>
					<span  class="none">585.56</span>
				</view>
				<image src="../../static/upsdk_payment_right.webp" mode=""></image>
			</view>
			<view class="btn" @click="GOPaymentRecords">
				查看更多
			</view>
		</view>
	</view>
</template>

<script>
	import loanTitleVue from '../../components/loan-Title.vue';
	import ListView from '@/components/ListView.vue'
	export default {
		data() {
			return {
				TitleImage:"../../static/back_black.png",
				rigthIcon:['../../static/boc_folder_title_service.png','../../static/icon_share_black.png'],
				FeelFreeLoanlist:[
					{name:'额度详情',icon:'../../static/LoanDataliTow-icon-1.png'},
					{name:'提前还款',icon:'../../static/LoanDataliTow-icon-2.png'},
					{name:'变更还款账户',icon:'../../static/LoanDataliTow-icon-3.png'},
					{name:'查看合同',icon:'../../static/LoanDataliTow-icon-4.png'},
					{name:'用款申请进度',icon:'../../static/LoanDataliTow-icon-5.png'},
				],
				FeelFreeLoanlistTow:[
					{name:'已结清贷款',icon:'../../static/LoanDataliTow-icon-6.png'},
					{name:'贷款机构',icon:'../../static/LoanDataliTow-icon-7.png'},
				],
				CreditB:{
					TotalBalance:'200,000.00',
					Money:'200,000.00',
					remaining:'0.00',
					Credit:[
						{name:'还款账户',text:'6216 ****** 6429',menu:'更改'},
						{name:'还款日',text:'每月11日'},
						{name:'年利率(单利)',text:'3.4%'},
						{name:'额度到期日',text:'2027/11/08'},
						{name:'贷款额度号',text:'PF533850000047334650473'},
						{name:'额度状态',text:'生效'},
						{name:'贷款机构名称',text:'中国银行广州大岭支行'},
						{name:'贷款机构地址',text:'广州市南沙区江南路110号首层、二层'},
						{name:'贷款机构电话',text:'02084987481'},
					],
				},
				scrollTop:0
			};
		},
		components:{
			loanTitleVue,
			ListView
		},
		methods:{
			Next(){
				uni.navigateTo({
					url:'/pages/LoanDataliTow/LoanDataliTow?id=2'
				})
			},
			GoNext(index){
				if(index === 0){
					uni.setStorageSync('Credit',this.CreditB),
					uni.navigateTo({
						url:'/pages/CreditDetails/CreditDetails'
					})
				}
				index === 1 ? uni.navigateTo({
					url:'/pages/Repayment/Repayment'
				}) : ''
				
				index === 3 ? uni.navigateTo({
					url:'/pages/contract/contract'
				}) : ''
			},
			GOPaymentRecords(){
				uni.navigateTo({
					url:'/pages/PaymentRecords/PaymentRecords?id=3'
				})
			}
		},
		onPageScroll(Scroll) {
			this.scrollTop =  Scroll.scrollTop
		},
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
				// border-bottom:1px solid #ddd ;
				padding: 40rpx 0;
				p{
					font-size: 25rpx;
				}
				.money{
					text-align: center;
					width: 100%;
					font-size: 60rpx;
					font-weight: bold;
					margin: 20rpx auto;
					// color: #daa969;
					span{
						font-size: 45rpx;
					}
				}
				.date{
					font-size: 28rpx;
					display: flex;
					align-items: center;
					image{
						width: 30rpx;
						height: 30rpx;
						margin:0 10rpx;
						margin-top: 10rpx;
					}
				}
			}
			.ListView-btn{
				display: flex;
				justify-content: space-between;
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
				display: flex;
				justify-content: space-between;
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
				align-items: center;
				.Row{
					display: flex;
					align-items: center;
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
				image{
					width: 80rpx;
					height: 60rpx;
					padding: 20rpx;
				}
			}
			.btn{
				margin-top: 20rpx;
				padding-top: 20rpx;
				text-align: center;
				border-top:1px solid #ddd ;
				font-size: 25rpx;
				color: #1572f0;
			}
		}
		swiper{
			::v-deep.uni-swiper-dot{
				// display: none;
				width: 15rpx;
				height: 5rpx;
				border-radius: 5rpx;
			}
			height: 150rpx;
			.FeelFreeLoan-ListView{
			}
		}
		.drawMoney-guangao{
			width: 95%;
			border-radius: 20rpx;
			margin: 0 auto;
			margin-top: 20rpx;
			background-color: #fff5e2;
			display: flex;
			align-items: center;
			image{
				padding: 20rpx;
				width: 90rpx;
				height: 90rpx;
			}
			.guangao{
				flex: 1;
				display: flex;
				align-items: center;
				flex-wrap: wrap;
				font-size: 28rpx;
				p{
					font-weight: bold;
				}
				view{
					display: flex;
					margin-top: 10rpx;
					align-items: center;
					font-size: 25rpx;
					width: 100%;
				}
				image{
					padding:0;
					width: 30rpx;
					height: 30rpx;
					margin-left: 10rpx;
				}
			}
			.btn{
				font-size: 25rpx;
				border: 1px solid #faa88e;
				color: #f65938;
				padding: 10rpx 20rpx;
				border-radius: 50rpx;
				margin-right: 20rpx;
			}
		}
		
	}
</style>
