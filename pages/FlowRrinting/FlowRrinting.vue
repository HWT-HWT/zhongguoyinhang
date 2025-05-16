<template>
	<view class="Flow-printing">
		<view class="Transaction-details-title">
			<loanTitleVue :TitleImage='TitleImage' name="交易流水打印" Color="#fff" ></loanTitleVue>
		</view>
		<view class="Flow-printing-view">
			<ListViewVue :listTitle="printList" width="33%" Pad="20rpx 0"></ListViewVue>
			<view class="SubTitle">
				<p>在线申请下载</p>
				<p>敏感数据保护</p>
				<p>支持溯源验真</p>
			</view>
			<view class="debtStep-nextStep" @click="Next()">
				立即申请
			</view>
			<view class="record">
				申请记录
			</view>
		</view>
		<view class="Loan-Datali-foot-btn">
			温馨提示: <br>
			1.支持生成已关联借记卡十年内交易流水文件，单次查询跨度不超过一年，每日支持申请五次。<br>
			2.若您在查询跨度内的交易流水条目较多(超过3500条)会导致生成的PDF文档容量过大，此时建议您缩小时间跨度或.. <br>
		</view>
	</view>
</template>

<script>
	import loanTitleVue from '../../components/loan-Title.vue';
	import ListViewVue from '../../components/ListView.vue';
	export default {
		data() {
			return {
				TitleImage:"../../static/back_black_white.png",
				printList:[
					{name:'足不出户',icon:'../../static/print-icon-1.png'},
					{name:'安全保障',icon:'../../static/print-icon-2.png'},
					{name:'银行认证',icon:'../../static/print-icon-3.png'}
				]
			};
		},
		components:{
			loanTitleVue,
			ListViewVue
		},
		methods:{
			Next(){
				uni.navigateTo({
					url:'/pages/PrintApplication/PrintApplication'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.Flow-printing{
		width: 100vw;
		height: 100vh;
		background:url('@/static/print-bg-1.png') no-repeat;
		background-size: 100% 100%;
		.Flow-printing-view{
			width: 95%;
			margin: 0 auto;
			background-color: #fff;
			border-radius: 10rpx;
			padding: 30rpx 0;
			margin-top: 260rpx;
			box-shadow: 0 0 10rpx 1rpx rgba(0, 0, 0, .1);
			.SubTitle{
				display: flex;
				font-size: 25rpx;
				justify-content: space-between;
				color: #888;
				p{
					margin-top: 5rpx;
					width: 33%;
					text-align: center;
				}
			}
			.debtStep-nextStep{
				display: flex;
				align-items: center;
				width: 90%;
				margin: 0 auto;
				margin-top: 50rpx;
				color: #fff;
				justify-content: center;
				padding: 20rpx 0;
				border-radius: 10rpx;
				background:linear-gradient(to right , #72b6fd ,#3e93ea) ;
			}
			.record{
				display: flex;
				align-items: center;
				width: 90%;
				margin: 0 auto;
				margin-top: 20rpx;
				color: #4a6ea0;
				justify-content: center;
				padding: 20rpx 0;
				border-radius: 10rpx;
				border: 1px solid;
				
			}
		}
		.Loan-Datali-foot-btn{
			width: 95%;
			margin: 0 auto;
			display: flex;
			align-items: center;
			margin-top: 40rpx;
			font-size: 25rpx;
			line-height: 40rpx;
			color: #888;
		}
	}
</style>
