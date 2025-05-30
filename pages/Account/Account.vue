<template>
	<view class="account">
		<view class="account-title">
			<loanTitleVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' :name='"账户总览"'></loanTitleVue>
		</view>
		<view class="account-Datali">
			<view class="Datali-Text">
				<view class="money">总资产(折算人民币元) <image v-if="Eye" @click="ClickEye" src="@/static/EyeColor.png" mode=""></image>   <image v-else @click="ClickEye" src="@/static/Eye.png" mode=""></image></view>
				<view class="money p" @click="GoAssets">{{!Eye ? '******': '51,602.48'}} <image src="../../static/upsdk_payment_right.webp" mode=""></image> </view>
				<view class="money span" @click="GoAssets">昨日收益(元)暂无收益 <image src="../../static/upsdk_payment_right.webp" mode=""></image> </view>
			</view>
			<image src="@/static/upsdk_mp_help.webp" mode=""></image>
		</view>
		<view class="account-card">
			<view class="card-title">
				<p>中行卡</p>
				<image src="@/static/boc_reload_black.png" mode=""></image>
			</view>
			<CardBox :id="1" :list-btn="['交易明细','转账','买理财']" card-name="0613 ****** 0716" sub-name="长城电子借记卡(II类账户)" money='51,602.48' @Next="Next" :Eye='Eye'></CardBox>
			<CardBox :id="2"  :list-btn="['交易明细','转账','买理财']" card-name="6216 ****** 9190" sub-name="长城电子借记卡(I类账户)" money='0.00' @Next="Next" :Eye='Eye'></CardBox>
		</view>
		<view class="aoocunt-addCard">
			<p>+ 手动添加卡/账户</p>
			<span>添加您的中行账户、数字钱包</span>
		</view>
	</view>
</template>

<script>
	import loanTitleVue from '../../components/loan-Title.vue';
	import CardBox from '@/components/card-Box.vue'
	export default {
		data() {
			return {
				TitleImage:"../../static/back_black.png",
				rigthIcon:['../../static/boc_folder_title_service.png','../../static/icon_share_black.png'],
				Eye:false,
			};
			
		},
		components:{
			loanTitleVue,
			CardBox
		},
		methods:{
			Next(obj){
				obj.index === 0 ? uni.navigateTo({
					url:'/pages/TransactionDetails/TransactionDetails'
				}):''
			},
			GoAssets(){
				uni.navigateTo({
					url:'/pages/assets/assets'
				})
			},
			ClickEye(){
				this.Eye = !this.Eye
			}
		}
	}
</script>

<style lang="scss">
	.account{
		width: 100vw;
		height: 100vh;
		background-color: #f7f7f7;
		.account-title{
			background-color: #fff;
			padding-bottom: 20rpx;
		}
		.account-Datali{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			background: url('@/static/account-bg-1.png');
			background-size:100% 100% ;
			display: flex;
			box-shadow: 0 0 10rpx 1rpx rgba(0, 0, 0, .1);
			justify-content: space-between;
			image{
				padding: 20rpx;
				width: 40rpx;
				height: 40rpx;
			}
			.Datali-Text{
				padding: 20rpx;
				.money{
					display: flex;
					align-content: center;
					font-size: 30rpx;
					image{
						padding:0;
						margin-left: 20rpx;
					}
				}
				.p{
					font-size: 50rpx;
					display: flex;
					align-content: center;
					margin:  20rpx auto;
					image{
						width: 65rpx;
						height: 65rpx;
					}
				}
				.span{
					font-size: 30rpx;
					display: flex;
					align-content: center;
					margin:  20rpx auto;
					line-height: 65rpx;
					image{
						width: 65rpx;
						height: 65rpx;
					}
				}
			}
			
		}
		.account-card{
			width: 90%;
			margin: 0 auto;
			.card-title{
				width: 100%;
				display: flex;
				justify-content: space-between;
				margin-top: 20rpx;
				align-items: center;
				p{
					color: #888;
				}
				image{
					width: 40rpx;
					height: 40rpx;
				}
			}
		}
		.aoocunt-addCard{
			width: 90%;
			margin: 0 auto;
			box-shadow: 0 0 10rpx 1rpx rgba(0, 0, 0, .1);
			padding: 20rpx 0;
			display: flex;
			flex-wrap: wrap;
			justify-content: center;
			margin-top: 20rpx;
			border-radius: 20rpx;
			p{
				width: 100%;
				text-align: center;
				color: #6c8edf;
				font-size: 35rpx;
			}
			span{
				font-size: 28rpx;
				color: #666;
				margin-top: 10rpx;
			}
		}
	}
</style>
