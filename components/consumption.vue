<template>
	<view class="consumption">
		<loanTitleVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' :name='name' :Scollor='TopTitle'></loanTitleVue>
		<view class="loan-Image">
			<image src="@/static/consumption-image-1.png" mode=""></image>
			<image src="@/static/consumption-image-2.png" mode=""></image>
		</view>
		<view class="loan-Product">
			<titleVue LFontSize="38" RColor="#888">
				<template #left>
					<view>优选产品</view>
				</template>
				<template #rigth >
					我是上班族 我要消费
				</template>
			</titleVue>
			<view class="Product-Row">
				<p>启航贷款</p>
				<span>最高额度</span>
				<p class="select">30,000.00</p>
				<span class="MiniSpan">入职可申请,还款负担小</span>
			</view>
			<view class="Product-Row">
				<p>好客贷</p>
				<span>最高额度</span>
				<p class="select">200,000.00</p>
				<span class="MiniSpan">全线上 无抵押 循环用</span>
			</view>
		</view>
		<view class="loan-Setting">
			<titleVue LFontSize="38" RColor="#888">
				<template #left>
					贷款小工具
				</template>
			</titleVue>
			<ListViewVue :listTitle="loanSetting" FontSize="25rpx" sizi='60rpx' width="25%" Pad='30rpx 0' @ClickNext='ClickNext'></ListViewVue>
		</view>
	</view>
</template>

<script>
	import backtaberVue from '../components/backtaber.vue';
	import occupyVue from '../components/occupy.vue';
	import titleVue from '../components/titleVue.vue';
	import ListViewVue from '../components/ListView.vue';
	import loanTitleVue from './loan-Title.vue';
	export default {
		name:"consumption",
		data() {
			return {
				TitleImage:"../../static/back_black.png",
				rigthIcon:['../../static/boc_folder_title_service.png','../../static/icon_share_black.png'],
				loanSetting:[
					{name:'贷款资金转出',icon:'../../static/loan-setting-1.png'},
					{name:'在线签约',icon:'../../static/loan-setting-2.png'},
					{name:'视频面谈',icon:'../../static/loan-setting-3.png'},
					{name:'申请进度查询',icon:'../../static/loan-setting-4.png'},
					{name:'征信查询',icon:'../../static/loan-setting-5.png'},
					{name:'贷款计算器',icon:'../../static/loan-setting-6.png'},
					{name:'额度查询',icon:'../../static/loan-setting-7.png'},
					{name:'贷款记录',icon:'../../static/loan-setting-8.png'},
				],
			};
		},
		components:{
			titleVue,
			ListViewVue,
			occupyVue,
			loanTitleVue,
			backtaberVue
		},
		props:{
			name:{
				type:String
			},
			TopTitle:{
				type:Number
			}
		},
		methods:{
			ClickNext(index){
				console.log(index);
				index === 3 ? uni.navigateTo({
					url:'/pages/ApplicationStatus/ApplicationStatus'
				}) : ''
				index === 6 ? uni.navigateTo({
					url:'/pages/LimitInquiry/LimitInquiry'
				}) : ''
				index === 7 ? uni.navigateTo({
					url:'/pages/LoanRecords/LoanRecords'
				}) : ''
			}
		}
	}
</script>

<style lang="scss">
	.consumption{
		width: 100%;
		padding-bottom: 100rpx;
		background: url('@/static/consumption-bg-1.png')no-repeat;
		background-size: 100% 400rpx;
		background-color: #fff;
		.loan-Image{
			width: 90%;
			margin: 0 auto;
			
			margin-top: 280rpx;
			image{
				width: 100%;
				height: 230rpx;
				margin-top: 10rpx;
			}
		}
		.loan-Product{
			width: 90%;
			margin: 0 auto;
			display: flex;
			flex-wrap:wrap;
			align-items: center;
			justify-content: space-between;
			.Product-Row{
				width: 49%;
				background-color: #fafafa;
				border-radius:20rpx;
				display: flex;
				align-items: center;
				text-align: center;
				flex-wrap: wrap;
				padding: 20rpx 0;
				p{
					width: 100%;
					font-size: 38rpx;
					margin: 10rpx 0;
					font-weight: bold;
				}
				span{
					width: 100%;
					font-size: 30rpx;
					color: #555;
				}
				.select{
					color: #a80000;
					font-size: 50rpx;
				}
				.MiniSpan{
					font-size: 25rpx;
				}
			}
		}
		.loan-Setting{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
		}
	}
</style>