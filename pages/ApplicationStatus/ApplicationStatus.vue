<template>
	<view class="ApplicationStatus">
		<view class="Transaction-details-title">
			<loanTitleVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' :name='"贷款申请进度"' ></loanTitleVue>
		</view>
		<view class="Transaction-details-Text">
			<span>近3个月查询结果</span>
			<view>筛选 <image src="@/static/boc_select_gray.png" mode=""></image> </view>
		</view>
		<view class="overdue">
			<image src="@/static/current_have_nothing.png" mode=""></image>
			<p>暂无申请记录</p>
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
			};
		},
		components:{
			loanTitleVue
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
	}
</style>
