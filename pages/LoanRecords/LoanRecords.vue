<template>
	<view class="Loan-records">
		<view class="Transaction-details-title">
			<loanTitleVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' :name='"贷款记录"' ></loanTitleVue>
		</view>
		<view class="MyLoan-ListView" v-for="(item,index) in LoanRecordsList" :key="index">
			<view class="ListView-Text" >
				<view class="ListView-title">
					<p>{{item.title}}</p>
				</view>
				<view class="assets-Datali">
					<view class="Row">
						<view class="p">下一还款日 </view>
						<span>{{item.NextDate}}</span>
					</view>
					<view class="Row" style="border: none;">
						<view class="p">应还</view>
						<span  class="none">{{item.NextMoney}}</span>
					</view>
				</view>
				<view class="assets-Datali">
					<view class="Row">
						<view class="p">用款日 </view>
						<span>{{item.Date}}</span>
					</view>
					<view class="Row" style="border: none;">
						<view class="p">用款金额</view>
						<span >{{item.Money}}</span>
					</view>
				</view>
			</view>
			
			<view class="ListView-btn">
				<view class="btn">
					到期还款
				</view>
				<view class="btn" style="border: none; color: #2c70ed;">
					提前还款申请
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
				rigthIcon:['../../static/boc_folder_title_service.png','../../static/icon_share_black.png'],
				LoanRecordsList:[
					{title:'随心智贷',NextDate:'2025/06/11',Date:'2024/11/13',NextMoney:'585.56',Money:'200,000.00'},
					{title:'中银E贷·经营贷',NextDate:'2025/06/01',Date:'2024/11/08',NextMoney:'6,518.09',Money:'900,000.00'},
				]
			};
		},
		components:{
			loanTitleVue
		}
	}
</script>

<style lang="scss" scoped>
	.Loan-records{
		width: 100vw;
		height: 100vh;
		background-color: #f4f4f4;
		.Transaction-details-title{
			background-color: #fff;
			font-weight: bold;
		}
		.MyLoan-ListView{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			border-radius: 20rpx;
			background-color: #fff;
			padding: 20rpx 0;
			.ListView-title{
				width: 100%;
				padding: 20rpx;
				font-size: 35rpx;
				line-height: 60rpx;
				.SubTitle{
					font-size: 30rpx;
					color: #888;
				}
				.isTrue{
					font-size: 50rpx;
				}
			}
			.assets-Datali{
				width: 100%;
				margin: 0 auto;
				color: #000;
				display: flex;
				margin-bottom: 30rpx;
				.Row{
					display: flex;
					align-items: center;
					flex-wrap: wrap;
					width: 50%;
					line-height: 60rpx;
					padding-left: 50rpx;
					.p{
						display: flex;
						align-items: center;
						justify-content: center;
						color: #888;
						width: 100%;
						font-size: 30rpx;
					}
					span{
						width: 100%;
						font-size: 36rpx;
						color: #000;
						font-weight: bold;
						text-align: center;
					}
					.none{
						color: #ff0000;
					}
				}
			}
			.ListView-btn{
				width: 100%;
				display: flex;
				margin-top: 20rpx;
				font-size: 30rpx;
				border-top: 1px solid #ddd;
				.btn{
					width: 50%;
					margin-top: 20rpx;
					text-align: center;
					border-right: 1px solid #ccc;
					font-weight: bold;
				}
			}
		}
	}
</style>
