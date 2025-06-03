<template>
	<view class="AccountOverview">
		<view class="AccountOverview-topTitle">
			<loanTitleVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' name="账户总览"  ></loanTitleVue>
		</view>
		<view class="AccountOverview-money">
			<view class="Title-Eye">
				<p>总资产(折算人民币元)</p>
				<image src="@/static/boc_finance_eye_open.png" mode=""></image>
			</view>
			<view class="money" @click="Next">
				45,084.39 <image src="../../static/upsdk_payment_right.webp" mode=""></image>
			</view>
			<view class="Footer">
				<p>昨日收益(元)暂无收益</p>
				<image src="@/static/upsdk_payment_right.webp" mode=""></image>
			</view>
		</view>
		<view class="AccountOverview-cardTitle">
			<p>中行卡</p>
			<image src="@/static/boc_reload_black.png" mode=""></image>
		</view>
		<view class="AccountOverview-card" style="background-color: #fff;">
			<view class="card-icon">
				<image src="@/static/AccountOverview-bg-2.png" mode=""></image>
				<view class="card-number">
					<p>6516 ****** 6429</p>
					<span>长城电子借记卡(I类账户)</span>
				</view>
			</view>
			<view class="money">
				<p>账面余额</p>
				<span>人民币元 <text>45,084.39</text> </span>
			</view>
			<view class="card-list">
				<view class="listView" v-for="(item,index) in cardList" :key="index" :style="{borderRight:index === 2 ? 'none':'1px solid #ddd'}" @click="Getindex(index)">
					{{item}}
				</view>
			</view>
		</view>
		<view class="AccountOverview-cardTitle">
			<p>未关联至电子银行账户</p>
			<image src="@/static/upsdk_mp_help.webp" mode=""></image>
		</view>
		
		<AccountCardVue :list='card' ></AccountCardVue>
		
		<view class="AccountOverview-AddCard">
			<p>+手动添加卡/账户</p>
			<span>添加您的中行账户、数字钱包</span>
		</view>
	</view>
</template>

<script>
	import loanTitleVue from '../../components/loan-Title.vue';
	import AccountCardVue from '../../components/AccountCard.vue';
	export default {
		data() {
			return {
				TitleImage:"../../static/back_black.png",
				rigthIcon:['../../static/boc_folder_title_service.png'],
				cardList:['交易明细','转账','买理财'],
				card:[
					{
						number:'6217 ****** 0911',
						SubNumber:'长城电子借记卡'
					},
					{
						number:'6216 ****** 6119',
						SubNumber:'长城电子借记卡'
					},
					{
						number:'7172 ****** 9244',
						SubNumber:'长城电子借记卡'
					}
				]
			};
		},
		components:{
			loanTitleVue,
			AccountCardVue
		},
		methods:{
			Next(){
				uni.navigateTo({
					url:'/pages/assets/assets'
				})
			},
			Getindex(index){
				index === 0 ? uni.navigateTo({
					url:'/pages/AccountDatails/AccountDatails'
				}) : ''
				index === 1 ? uni.navigateTo({
					url:'/pages/AccountTransfer/AccountTransfer'
				}) : ''
			}
		}
	}
</script>

<style lang="scss" scoped>
.AccountOverview{
	width: 100vw;
	min-height: 100vh;
	background-color: #f4f4f4;
	.AccountOverview-topTitle{
		background-color: #fff;
	}
	.AccountOverview-money{
		width: 90%;
		height: 300rpx;
		background:url('@/static/AccountOverview-bg-1.png');
		margin: 0 auto;
		background-size: 100% 100%;
		margin-top: 20rpx;
		color: #603000;
		.Title-Eye{
			padding: 40rpx;
			display: flex;
			align-items: center;
			p{
				font-size: 28rpx;
			}
			image{
				width: 40rpx;
				height: 40rpx;
				margin-left: 20rpx;
			}
		}
		.money{
			padding:0 40rpx;
			display: flex;
			align-items: center;
			font-size: 45rpx;
			font-weight: bold;
			image{
				width: 60rpx;
				height: 60rpx;
			}
		}
		.Footer{
			padding: 40rpx;
			display: flex;
			align-items: center;
			p{
				font-size: 28rpx;
			}
			image{
				width: 60rpx;
				height: 60rpx;
				margin-left: 20rpx;
			}
		}
	}
	.AccountOverview-cardTitle{
		width: 90%;
		margin: 20rpx auto;
		display: flex;
		align-items: center;
		font-size: 25rpx;
		justify-content: space-between;
		image{
			width:30rpx;
			height: 30rpx;
		}
	}
	.AccountOverview-card{
		width: 90%;
		margin: 0 auto;
		margin-top: 20rpx;
		border-radius: 20rpx;
		.card-icon{
			padding: 30rpx;
			display: flex;
			align-items: center;
			image{
				width: 120rpx;
				height: 80rpx;
			}
			.card-number{
				flex: 1;
				margin-left: 20rpx;
				p{
					font-size: 25rpx;
					font-weight: bold;
				}
				span{
					font-size: 23rpx;
				}
			}
			text{
				font-size: 25rpx;
				color:#376fd3 ;
			}
		}
		.money{
			padding: 30rpx;
			background-color: #fbf8f1;
			display: flex;
			justify-content: space-between;
			font-size: 25rpx;
			color: #666665;
			span{
				font-weight: bold;
				text{
					margin-left: 10rpx;
					color: #000;
				}
			}
			
		}
		.card-list{
			display: flex;
			align-items: center;
			justify-content: space-between;
			padding: 20rpx 0;
			.listView{
				font-size: 28rpx;
				width: 33%;
				border-right:1px solid #ddd;
				text-align: center;
			}
		}
	}
	.AccountOverview-AddCard{
		width: 90%;
		margin: 40rpx auto;
		background-color: #fff;
		display: flex;
		flex-wrap: wrap;
		padding: 20rpx 0;
		justify-content:center;
		border-radius: 20rpx;
		font-size: 25rpx;
		p{
			margin-bottom: 10rpx;
			font-size: 28rpx;
			color: #376fd3;
			width: 100%;
			text-align: center;
		}
		
	}
}
</style>
