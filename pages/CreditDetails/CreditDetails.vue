<template>
	<view class="Loan-Datali">
		<view class="Loan-Datali-Tab">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' :RightMax='1' :isText='false' Color="#000">
				额度详情
			</backtaberVue>
		</view>
		<view class="Loan-Datali-MaxTitle">
			<view class="MaxText">
				<p>总额度(人民币元)</p>
				<span>{{Credit.TotalBalance}}</span>
			</view>
			<view class="SubText">
				<view class="Text">
					<p>已用额度(人民币元)</p>
					<span>{{Credit.Money}}</span>
				</view>
				<view class="Text">
					<p>可用额度(人民币元)</p>
					<span>{{Credit.remaining}}</span>
				</view>
			</view>
		</view>
		<view class="Loan-Datali-ListView">
			<view class="ListView" v-for="(item,index) in Credit.Credit " :key="index">
				<view class="name">
					{{item.name}}
				</view>
				<view class="text">
					{{item.text}}
				</view>
				<view class="menu" v-if="item.menu">
					{{item.menu}}
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	import backtaberVue from '../../components/backtaber.vue'
	export default {
		data() {
			return {
				TitleImage:"../../static/back_black.png",
				rigthIcon:['../../static/boc_folder_title_service.png'],
				Credit:''
			}
		},
		components:{
			occupyVue,
			backtaberVue
		},
		methods: {
			
		},
		created() {
			this.Credit = uni.getStorageSync('Credit')
		}
	}
</script>

<style scoped lang="scss">
	.Loan-Datali{
		width: 100vw;
		height: 100vh;
		background-color: #f4f4f4;
		.Loan-Datali-Tab{
			background-color: #fff;
		}
		.Loan-Datali-MaxTitle{
			width: 100%;
			padding-bottom: 40rpx;
			background: url('@/static/LoanDatali-bg-1.png')no-repeat;
			background-size: 100% 300rpx;
			.MaxText{
				width: 100%;
				text-align: center;
				padding-top: 40rpx;
				p{
					font-size: 28rpx;
					color: #888;
				}
				span{
					width: 100%;
					font-size: 50rpx;
					color: #dc0034;
				}
			}
			.SubText{
				width: 85%;
				margin: 0 auto;
				display: flex;
				justify-content: space-between;
				margin-top: 40rpx;
				text-align: center;
				p{
					font-size: 25rpx;
					color: #888;
				}
				span{
					font-size: 35rpx;
				}
			}
		}
		.Loan-Datali-ListView{
			width: 100%;
			background-color: #fff;
			padding-bottom: 20rpx;
			.ListView{
				display: flex;
				font-size: 28rpx;
				padding: 20rpx;
				margin-top: 10rpx;
				.name{
					width: 30%;
					color: #888;
				}
				.text{
					flex: 1;
					font-size: 28rpx;
				}
				.menu{
					width: 10%;
					color: #1170f0;
				}
			}
		}
	}
</style>
