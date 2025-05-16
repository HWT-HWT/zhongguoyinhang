<template>
	<view class="more">
		<view class="drawMoney-tbas">
			<loanTitleVue name="更多" :TitleImage='TitleImage'></loanTitleVue>
		</view>
		<view class="more-ListView">
			<view class="more-list" @click="ClickGo">
				<p>额度详情</p>
				<image src="../../static/upsdk_payment_right.webp" mode=""></image>
			</view>
			<view class="more-list">
				<p>变更还款账户</p>
				<image src="../../static/upsdk_payment_right.webp" mode=""></image>
			</view>
			<view class="more-list">
				<p>提前还款</p>
				<image src="../../static/upsdk_payment_right.webp" mode=""></image>
			</view>
			<view class="more-list" @click="Next()">
				<p>用款记录</p>
				<image src="../../static/upsdk_payment_right.webp" mode=""></image>
			</view>
			<view class="more-list" @click="Golist">
				<p>查看合同</p>
				<image src="../../static/upsdk_payment_right.webp" mode=""></image>
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
			};
		},
		components:{
			loanTitleVue
		},
		methods:{
			Next(){
				uni.navigateTo({
					url:'/pages/PaymentRecords/PaymentRecords?id=1',
				})
			},
			ClickGo(){
				uni.navigateTo({
					url:'/pages/CreditDetails/CreditDetails'
				})
			},
			Golist(){
				uni.navigateTo({
					url:'/pages/contract/contract'
				})
			}
		}
	}
</script>

<style lang="scss">
	.more{
		width: 100vw;
		height: 100vh;
		background-color: #f7f7f7;
		.drawMoney-tbas{
			background-color: #fff;
		}
		.more-ListView{
			margin-top: 10rpx;
			.more-list{
				background-color: #fff;
				padding: 20rpx;
				display: flex;
				font-weight: bold;
				justify-content: space-between;
				border-bottom: 1px solid #f4f4f4;
				image{
					width: 50rpx;
					height: 50rpx;
				}
			}
		}
		
	}
</style>
