<template>
	<view class="ApplicationStatus">
		<view class="Transaction-details-title">
			<loanTitleVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' :name='"用款记录"' ></loanTitleVue>
		</view>
		<view class="Transaction-details-Text" v-if='!id'>
			<span>近3个月查询结果</span>
			<view>筛选 <image src="@/static/boc_select_gray.png" mode=""></image> </view>
		</view>
		<view class="Transaction-Text" v-else>
			<span>待还款,共1笔</span>
			<view>单位:人民币元</view>
		</view>
		
		<view class="overdue" v-if='!id'>
			<image src="@/static/current_have_nothing.png" mode=""></image>
			<p>没有符合条件的记录</p>
		</view>
		
		<view v-else>
			<view class="assets-Datali" @click="Next()" v-if='this.id == 1'>
				<view class="Row">
					<view class="p">2024/11/08用款</view>
					<span class="none">900,000.00</span>
				</view>
				<view class="Row" style="border: none;">
					<view class="p">2025/06/01应还</view>
					<span  class="none">6,518.09</span>
				</view>
				<image class="image" src="../../static/upsdk_payment_right.webp" mode=""></image>
			</view>
			
			<view class="assets-Datali" @click="Next(id)" v-if='this.id == 2 || this.id == 3'>
				<view class="Row">
					<view class="p">2024/11/13用款</view>
					<span class="none">200,000.00</span>
				</view>
				<view class="Row" style="border: none;">
					<view class="p">2025/06/08应还</view>
					<span  class="none">6,259.82</span>
				</view>
				<image class="image" src="../../static/upsdk_payment_right.webp" mode=""></image>
			</view>
			
			<view class="footView" @click="goSettle" v-if="this.id == 3 || this.id == 1">
				查看已结清
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
				id:0
			};
		},
		components:{
			loanTitleVue
		},
		onLoad(query) {
			this.id = query.id 
			console.log(this.id);
		},
		methods:{
			Next(id){
				if(id == 3){
					return uni.navigateTo({
						url:'/pages/LoanDataliTow/LoanDataliTow?id=2'
					})
				}
				if(this.id == 1){
					uni.navigateTo({
						url:'/pages/LoanDataliTow/LoanDataliTow'
					})
				}else{
					uni.navigateTo({
						url:'/pages/datalis/datalis'
					})
				}
				
			},
			goSettle(){
				uni.navigateTo({
					url:'/pages/settle/settle'
				})
			}
		}
	}
</script>

<style lang="scss">
	.ApplicationStatus{
		width: 100vw;
		height: 100vh;
		background-color: #f4f4f4;
		.Transaction-details-title{
			background-color: #fff;
		}
		.Transaction-details-Text{
			width: 90%;
			margin: 0 auto;
			display: flex;
			justify-content: space-between;
			align-items: center;
			margin-top: 20rpx;
			font-size: 28rpx;
			color: #666;
			margin-bottom: 20rpx;
			view{
				display: flex;
				align-items: center;
				image{
					margin-left: 20rpx;
					width: 30rpx;
					height: 30rpx;
				}
			}
		}
		.Transaction-Text{
			width: 90%;
			margin: 0 auto;
			display: flex;
			justify-content: space-between;
			align-items: center;
			margin-top: 20rpx;
			font-size: 28rpx;
			color: #000;
			margin-bottom: 20rpx;
			view{
				display: flex;
				align-items: center;
				image{
					margin-left: 20rpx;
					width: 30rpx;
					height: 30rpx;
				}
			}
		}
		.overdue{
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
		.assets-Datali{
			width: 100%;
			margin: 0 auto;
			background-color: #fff;
			color: #000;
			display: flex;
			padding: 20rpx 0;
			justify-content: space-between;
			align-items: center;
			.Row{
				display: flex;
				align-items: center;
				flex-wrap: wrap;
				width: 50%;
				padding-left: 50rpx;
				text-align: center;
				.p{
					display: flex;
					align-items: center;
					justify-content: center;
					color: #888;
					width: 100%;
					font-size: 28rpx;
					image{
						width: 40rpx;
						height: 40rpx;
					}
				}
				.none{
					width: 100%;
					font-size: 34rpx;
					color: #000;
					margin-top: 10rpx;
				}
			}
			.image{
				width: 50rpx;
				height: 50rpx;
			}
		}
		.footView{
			width: 100vw;
			display: flex;
			justify-content: center;
			padding: 30rpx 0;
			background-color: #fff;
			color:#1170f0;
			position: fixed;
			bottom: 0;
		}
	}
</style>
