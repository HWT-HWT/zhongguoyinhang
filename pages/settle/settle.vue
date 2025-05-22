<template>
	<view class="ApplicationStatus">
		<view class="Transaction-details-title">
			<loanTitleVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' :name='"已结清用款"' ></loanTitleVue>
		</view>
		<view >
			<view class="overdue">
				<image src="@/static/current_have_nothing.png" mode=""></image>
				<p>无已结清用款记录</p>
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
				tabListOne: ['待还款','已还款'],
				index:1,
				showView:true
			};
		},
		components:{
			loanTitleVue
		},
		methods:{
			SetIndex(index){
				this.index = index
			}
		},
		onLoad(parma) {
			console.log(parma.id == 2);
			if(parma.id){
				this.showView = false 
				this.index = 2
			}else{
				this.showView = true
				this.index = 1
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
		.repayment-prompt{
			width: 100%;
			margin: 0 auto;
			font-size: 28rpx;
			background-color: #f5f9fe;
			display: flex;
			align-items: center;
			p{
				color: #000;
				padding: 20rpx;
			}
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
		.title-btn{
			padding:0 50rpx;
			margin: 0 auto;
			background-color: #fff;
			display: flex;
			align-items: center;
			justify-content: center;
			view{
				padding: 20rpx 0 ;
				padding-bottom: 20rpx;
				margin: 0 20rpx;
				border-bottom:2px solid #fff;
				font-size: 25rpx;
			}
			.selectView{
				color: #a80000;
				border-bottom:2px solid;
			}
		}
		.ApplicationStatus-list{
			.time{
				background-color: #ddd;
				color: #888;
				font-size: 22rpx;
				padding:10rpx 20rpx;
				border-bottom: 1px solid #bdbdbd;
			}
			.li{
				display: flex;
				align-content: center;
				background-color: #ddd;
				.date{
					height: 20rpx;
					color: #888;
					display: flex;
					flex-wrap: wrap;
					justify-content: center;
					align-items: center;
					span{
						font-size: 30rpx;
						font-weight: bold;
					}
					p{
						text-align: center;
						width: 100%;
						font-size: 15rpx;
					}
				}
				.centent{
					width: 100%;
					background-color: #fff;
					.centent-view{
						font-size: 25rpx;
						padding: 15rpx;
						border-bottom: 1px solid #ddd;
					}
				}
			}
		}
	}
</style>
