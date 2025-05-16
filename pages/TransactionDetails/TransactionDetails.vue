<template>
	<view class="Transaction-details">
		<view class="Transaction-details-title">
			<loanTitleVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' :name='"交易明细"' :Scollor="Scroll"></loanTitleVue>
		</view>
		<view class="Transaction-details-card">
			<view class="Card-content">
				<image src="@/static/card-image-1.png" mode=""></image>
				<view class="content-text">
					<span>6216 ****** 9190</span>
					<p>长城电子借记卡(I类账户)</p>
				</view>
			</view>
		</view>
		<view class="Transaction-details-Text">
			<span>近6个月明细</span>
			<view>筛选 <image src="@/static/boc_select_gray.png" mode=""></image> </view>
		</view>
		<!-- <view class="Transaction-details-listView">
			<view class="title">
				10月/2024
			</view>
			<view class="ListView">
				<view class="Date">
					<p>01</p>
					<span>周二</span>
				</view>
				<view class="Datali">
					<view class="Datali-Row">
						<p>客户汇划</p>
						<span>余额0.00</span>
					</view>
					<view class="Datali-Row TextAlien">
						<p>中银消费金融有限公司</p>
						<span><text>人民币元</text>-82.64</span>
					</view>
				</view>
			</view>
		</view> -->
		<!-- <view class="Transaction-details-listView" v-for="(item,index) in 10" :key="index">
			<view class="title">
				10月/2024
			</view>
			<view class="ListView">
				<view class="Date">
					<p>01</p>
					<span>周二</span>
				</view>
				<view class="Datali">
					<view class="Datali-Row">
						<p>客户汇划</p>
						<span>余额0.00</span>
					</view>
					<view class="Datali-Row TextAlien">
						<p>中银消费金融有限公司</p>
						<span><text>人民币元</text>-82.64</span>
					</view>
				</view>
			</view>
		</view> -->
		
		<uni-popup ref="alertDialog" type="dialog">
			<uni-popup-dialog :type="msgType" :showClose='false' cancelText="关闭"  content="没有查询到符合条件的记录" @close="dialogClose"></uni-popup-dialog>
		</uni-popup>
	</view>
</template>

<script>
	import loanTitleVue from '../../components/loan-Title.vue';
	export default {
		data() {
			return {
				TitleImage:"../../static/back_black.png",
				rigthIcon:['../../static/boc_folder_title_service.png','../../static/icon_share_black.png'],
				Scroll:0,
				type: 'center',
				msgType: 'success',
			};
		},
		components:{
			loanTitleVue,
		},
		onPageScroll(Scroll) {
			this.Scroll = Scroll.scrollTop
		},
		mounted() {
			this.dialogToggle('info')
		},
		methods:{
			dialogToggle(type) {
				this.msgType = type
				this.$refs.alertDialog.open()
			},
			dialogClose(){
				this.$refs.alertDialog.close()
			}
		}
	}
</script>

<style lang="scss">
	.Transaction-details{
		width: 100vw;
		height: 100vh;
		background-color: #e8e9ed;
		.Transaction-details-title{
			background-color: #fff;
			padding-bottom: 20rpx;
		}
		.Transaction-details-card{
			width: 95%;
			margin: 0 auto;
			margin-top: 20rpx;
			.Card-content{
				display: flex;
				margin: 0 auto;
				align-items: center;
				padding: 30rpx;
				background-color: #fff;
				border-radius: 10rpx;
				image{
					width: 100rpx;
					height: 80rpx;
				}
				.content-text{
					margin-left: 20rpx;
					font-size: 32rpx;
					p{
						color: #666;
					}
				}
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
		.Transaction-details-listView{
			width: 100%;
			.title{
				padding: 15rpx 35rpx;
				background-color: #f9f9f9;
				font-size: 28rpx;
				color: #555;
			}
			.ListView{
				width: 100%;
				display: flex;
				.Date{
					display: flex;
					flex-wrap: wrap;
					justify-content: center;
					align-items: center;
					padding: 20rpx 10rpx;
					text-align: center;
					background-color: #f8faf9;
					p{
						font-size: 35rpx;
					}
					span{
						width: 100%;
						font-size: 20rpx;
					}
				}
				.Datali{
					flex: 1;
					padding: 20rpx;
					display: flex;
					align-items: center;
					background-color: #fff;
					justify-content: space-between;
					text-align: center;
					line-height: 50rpx;
					.Datali-Row{
						p{
							font-size: 30rpx;
						}
						span{
							font-size: 28rpx;
							color: #888;
						}
					}
					.TextAlien{
						text-align: right;
						p{
							font-size: 28rpx;
							color: #666;
						}
						span{
							text{
								color: #000;
								margin-right: 10rpx;
							}
						}
					}
				}
				
			}
		}
	}
</style>
