<template>
	<view class="assets">
		<view class="assets-title">
			<loanTitleVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' name="资产管理" Color="#fff" ></loanTitleVue>
		</view>
		<view class="assets-SubTitle">
			<p>等情况,仅供参考,不作为对账凭证。</p>
		</view>
		<view class="assets-MaxTitle">
			<p>我的资产</p>
			<span>(折算成人民币元)</span>
			<image v-if="Eye" src="@/static/assets_eye_close.png" mode="" @click="ClickEye"></image>
			<image v-else src="@/static/assets_eye_open.png" mode="" @click="ClickEye"></image>
		</view>
		<view class="assets-Date">
			{{oldTime}}<image src="@/static/boc_reload.png" mode=""></image>
		</view>
		<view class="assets-Money">
			<view class="Row Select">
				<p>总资产</p>
				<span>{{Eye ? '******': '18,600.00'}}</span>
			</view>
			<view class="Row" style="border: none;">
				<p>总负债</p>
				<span>{{Eye ? '******': '1,100,000.00'}}</span>
			</view>
		</view>
		<view class="assets-Chatting">
			<p>昨日收益</p>
			<image class="img" src="@/static/icon_assets_triangle.png" mode=""></image>
			<view class="span">{{Eye ? '******': '0.00'}} <image src="@/static/upsdk_payment_right.webp" mode=""></image> </view>
		</view>
		<view class="assets-Datali">
			<view class="Row">
				<view class="p">活期存款 <image src="@/static/upsdk_payment_right.webp" mode=""></image> </view>
				<span>{{Eye ? '******': '0.00'}}</span>
			</view>
			<view class="Row" style="border: none;">
				<view class="p">结构性存款 <image src="@/static/upsdk_payment_right.webp" mode=""></image> </view>
				<span>{{Eye ? '******': '0.00'}}</span>
			</view>
		</view>
		<view class="assets-Datali">
			<view class="Row">
				<view class="p">信用卡存款 <image src="@/static/upsdk_payment_right.webp" mode=""></image> </view>
				<span>{{Eye ? '******': '0.00'}}</span>
			</view>
			<view class="Row" style="border: none;">
				<view class="p">保险 <image src="@/static/upsdk_payment_right.webp" mode=""></image> </view>
				<span>{{Eye ? '******': '0.00'}}</span>
			</view>
		</view>
		<view class="assets-Datali">
			<view class="Row">
				<view class="p">定期存款 <image src="@/static/upsdk_payment_right.webp" mode=""></image> </view>
				<span class="none">您尚未持有，去看看</span>
			</view>
			<view class="Row" style="border: none;">
				<view class="p">理财 <image src="@/static/upsdk_payment_right.webp" mode=""></image> </view>
				<span  class="none">您尚未持有，去看</span>
			</view>
		</view>
		<view class="assets-Datali">
			<view class="Row">
				<view class="p">基金(含活钱宝) <image src="@/static/upsdk_payment_right.webp" mode=""></image> </view>
				<span class="none">您尚未持有，去看看</span>
			</view>
			<view class="Row" style="border: none;">
				<view class="p">代销资管 <image src="@/static/upsdk_payment_right.webp" mode=""></image> </view>
				<span  class="none">您尚未持有，去看</span>
			</view>
		</view>
		<view class="assets-menu">
			展开 <image src="@/static/bottom-1.png" mode=""></image>
		</view>
		<view class="assets-MyBranches">
			
			<view class="MyBranches-banner">
				<image src="@/static/assets-bg-1.png" mode=""></image>
			</view>
			
			<view class="MyBranches-Text">
				<span>资金归集</span>
				<span>资金规划</span>
				<span>签约管理</span>
			</view>
			
			<view class="asstes-foot">
				说明: <br>
				1.鉴于各产品系统数据更新时间存在差异性，资产管理功能中展示的相关资产、负债信息仅供参考，不作为对账凭据，具体以各产品系统记录为准。如您想获得最为准确的、实时的资产明细信息，请进入相关具体功能模块或前往我行营业网点查询 。<br>
				2.昨日收益数据为估算收益，仅供参考，实际收益以具体到账为准。纳入收益计算范围的产品目前包括:理财、代销资管、基金、结构性存款。<br>
				3.如您存在外币的资产、负债及收益信息，相关金额将被折算为人民币计算。<br>
				4.“定期存款”包括您在我行持有的整存整取、通知存款、零存整取、定活两便、存本取息等定期类存款。<br>
				5.部分仅在柜台销售的理财产品暂未包含在资产统计内，您可前往我行营业网点查询。<br>
				6.如需查询您通过跨境理财通专区购买的产品信息，请通过跨境理财通专区办理<br>
			</view>
		</view>
	</view>
</template>

<script>
	import backtaberVue from '../../components/backtaber.vue';
	import loanTitleVue from '../../components/loan-Title.vue';
	import occupyVue from '../../components/occupy.vue';
	export default {
		data() {
			return {
				TitleImage:"../../static/back_black_white.png",
				rigthIcon:['../../static/boc_folder_title_white_service.png','../../static/icon2.png'],
				Eye:true,
				Scroll:0,
				oldTime:''
			};
		},
		components:{
			backtaberVue,
			occupyVue,
			loanTitleVue
		},
		methods:{
			ClickEye(){
				this.Eye = !this.Eye
			}
		},
		onPageScroll(Scroll) {
			this.Scroll = Scroll.scrollTop
		},
		created() {
			this.oldTime = uni.getStorageSync('OldDate')
		}
	}
</script>

<style lang="scss" scoped>
	.assets{
		width: 100vw;
		height: 100vh;
		background: url('@/static/bg_assets_card.png')no-repeat;
		background-size: 1200rpx 550rpx;
		background-position:top right;
		.assets-SubTitle{
			width: 90%;
			margin: 0 auto;
			padding-top: 20rpx;
			font-size: 28rpx;
			color: #b0bac4;
		}
		.assets-MaxTitle{
			width: 90%;
			margin: 0 auto;
			color: #fff;
			display: flex;
			align-items: center;
			background-image: linear-gradient(to right, #f4e6d3, #f8dfb8); /* 线性渐变背景，方向向上 */
			-webkit-background-clip: text; /* 背景被裁剪成文字的前景色 */
			-webkit-text-fill-color: transparent; /* 文字填充颜色变透明 */   
			margin-top: 10rpx;
			p{
				font-size:40rpx;
				font-weight: bold;
			}
			span{
				font-size: 20rpx;
				margin: 0 5rpx;
				padding-top:20rpx;
			}
			image{
				width: 50rpx;
				height: 50rpx;
				padding-top:20rpx;
				margin-left: 10rpx;
			}
		}
		.assets-Date{
			width: 90%;
			margin: 0 auto;
			font-size: 25rpx;
			color: #b0bac4;
			margin-top: 10rpx;
			display: flex;
			align-items: center;
			image{
				margin-left: 10rpx;
				width: 35rpx;
				height: 35rpx;
			}
		}
		.assets-Money{
			width: 90%;
			margin: 0 auto;
			color: #fff;
			display: flex;
			.Row{
				display: flex;
				align-items: center;
				justify-content: center;
				border-right: 1px solid #888;
				flex-wrap: wrap;
				width: 50%;
				line-height: 60rpx;
				margin-top: 40rpx;
				p{
					text-align: center;
					width: 100%;
					font-size: 28rpx;
				}
				span{
					font-size: 35rpx;
					letter-spacing: 5rpx;
				}
			}
			.Select{
				color: #e6d5b2;
			}
		}
		.assets-Chatting{
			width: 85%;
			margin: 0 auto;
			background-color: #fff;
			display: flex;
			align-items: center;
			justify-content: space-between;
			padding: 20rpx;
			margin-top: 30rpx;
			border-radius: 10rpx;
			box-shadow: 0 0 10rpx 10rpx rgba(0, 0, 0, .1);
			p{
				width: 20%;
				font-size: 30rpx;
			}
			.img{
				width: 60rpx;
				height: 40rpx;
				position: relative;
				top: -40rpx;
				left: -180rpx;
			}
			.span{
				width: 20%;
				display: flex;
				font-size: 30rpx;
				letter-spacing: 2rpx;
				align-items: center;
				image{
					width: 40rpx;
					height: 40rpx;
				}
			}
		}
		.assets-Datali{
			width: 100%;
			margin: 0 auto;
			color: #000;
			display: flex;
			margin-top: 20rpx;
			.Row{
				display: flex;
				align-items: center;
				border-right: 1px solid #ddd;
				flex-wrap: wrap;
				width: 50%;
				line-height: 60rpx;
				margin-top: 40rpx;
				padding-left: 50rpx;
				.p{
					display: flex;
					align-items: center;
					color: #888;
					width: 100%;
					font-size: 28rpx;
					image{
						width: 40rpx;
						height: 40rpx;
					}
				}
				span{
					font-size: 35rpx;
				}
				.none{
					font-size: 25rpx;
					color: #888;
				}
			}
		}
		.assets-menu{
			display: flex;
			align-items: center;
			justify-content: center;
			font-size: 28rpx;
			margin-top: 40rpx;
			color: #666;
			image{
				margin-left: 5rpx;
				width: 60rpx;
				height: 60rpx;
				transform: scale(1);
			}
		}
		.assets-MyBranches{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			.MyBranches-banner{
				width: 100%;
				image{
					width: 100%;
					height: 180rpx;
					border: 1px solid #ddd;
					border-radius: 20rpx; 
				}
			}
			.MyBranches-Text{
				border: 1px solid #ddd;
				width: 90%;
				margin: 0 auto;
				margin-top: -20rpx;
				padding: 35rpx;
				display: flex;
				align-items: center;
				justify-content: space-between;
				font-size: 28rpx;
			}
		}
		.asstes-foot{
			width: 98%;
			margin: 0 auto;
			font-size: 24rpx;
			margin-top: 50rpx;
			color: #999;
		}
	}
</style>
