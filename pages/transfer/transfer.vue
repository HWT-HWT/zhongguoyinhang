<template>
	<view class="transfer">
		<view class="transfer-topTitle">
			<loanTitleVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' name="转账汇款"  ></loanTitleVue>
		</view>
		<view style="background-color: #fff; padding: 20rpx;">
			<view class="transfer-List">
				<ListViewVue :listTitle="list" width="33%" @ClickNext='ClickNext' ></ListViewVue>
				<view class="List-Btn">
					<view class="Btn">
						<image src="../../static/transfer-icon-4.png" mode=""></image> 预约转账
					</view>
					<view class="Btn">
						<image src="../../static/transfer-icon-5.png" mode=""></image> 转账记录
					</view>
				</view>
			</view>
		</view>
		<view class="transfer-Account">
			<titleVue :LFontW="false" LFontSize="38" RColor="#4674b6">
				<template #left>
					常用收款人
				</template>
				<template #rigth>
					全部
				</template>
			</titleVue>
		</view>
		<view class="transfer-Account-Datali">
			<view>
				<image src="@/static/transfer-Account-Datali-1.png" mode=""></image>
				<span>我的账户(5)</span>
			</view>
			<image class="bottom" src="@/static/bottom-3.png" mode=""></image>
		</view>
		<view class="transfer-Account-Name">
			<image src="../../static/boc_logo.png" mode=""></image>
			尾号 0716 长城电子借记卡
		</view>
		<view class="transfer-Account-Name">
			<image src="../../static/boc_logo.png" mode=""></image>
			尾号 0716 长城电子借记卡
		</view>
	</view>
</template>

<script>
	import loanTitleVue from '../../components/loan-Title.vue';
	import ListViewVue from '../../components/ListView.vue';
	import titleVue from '../../components/titleVue.vue';
	export default {
		data() {
			return {
				TitleImage:"../../static/back_black.png",
				rigthIcon:['../../static/boc_folder_title_service.png','../../static/icon_share_black.png'],
				list:[
					{name:'账号转账',icon:'../../static/transfer-icon-1.png'},
					{name:'手机转账',icon:'../../static/transfer-icon-2.png'},
					{name:'跨境转账',icon:'../../static/transfer-icon-3.png'}
				]
			};
		},
		components:{
			loanTitleVue,
			ListViewVue,
			titleVue
		},
		methods:{
			ClickNext(index){
				index === 0 ? uni.navigateTo({
					url:'/pages/AccountTransfer/AccountTransfer'
				}) : ''
				
			}
		}
	}
</script>

<style lang="scss" scoped>
	.transfer{
		width: 100vw;
		height: 100vh;
		background-color: #f4f4f4;
		.transfer-topTitle{
			background-color: #fff;
		}
		.transfer-List{
			width: 90%;
			margin: 0 auto;
			padding-top: 30rpx;
			background-color: #fff;
			margin-top: 20rpx;
			border-radius: 20rpx;
			background: linear-gradient(to right ,#f4e7d4 , #e7d6bc);
			box-shadow: 0 0 10rpx 1rpx rgba(0, 0, 0, .1);
			.List-Btn{
				width: 100%;
				background-color: #fff;
				margin-top: 20rpx;
				border-radius:0 0 20rpx 20rpx;
				display: flex;
				.Btn{
					padding:30rpx 0;
					width: 50%;
					display: flex;
					align-items: center;
					font-size: 28rpx;
					justify-content: center;
					image{
						width: 40rpx;
						height: 40rpx;
						margin-right: 5rpx;
					}
				}
			}
		}
		.transfer-Account{
			margin: 0 auto;
			padding:0 50rpx;
			border-bottom:1px solid #ddd;
			background-color: #fff;
			margin-top: -10rpx;
		}
		.transfer-Account-Datali{
			margin: 0 auto;
			display: flex;
			align-items: center;
			justify-content: space-between;
			padding:20rpx 40rpx;
			background-color: #fff;
			border-bottom:1px solid #ddd;
			view{
				display: flex;
				align-items: center;
				font-size: 34rpx;
				image{
					width: 80rpx;
					height: 80rpx;
					margin-right: 20rpx;
				}
			}
			
			.bottom{
				width: 40rpx;
				height: 40rpx;
			}
		}
		.transfer-Account-Name{
			display: flex;
			align-items: center;
			color: #888;
			font-size: 30rpx;
			padding: 20rpx 40rpx;
			border-bottom: 1px solid #ddd;
			image{
				width: 70rpx;
				height: 70rpx;
				margin-right: 20rpx;
			}
		}
	}
</style>
