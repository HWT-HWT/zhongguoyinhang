<template>
	<view class="accountDatails">
		<view class="accountDatails-title">
			<loanTitleVue :TitleImage='TitleImage'  :name='"交易明细"' :Scollor='TopTitle'></loanTitleVue>
		</view>
		
		<view class="accountDatails-card">
			<AccountCardVue :list="list" :btn="false"></AccountCardVue>
		</view>
		
		<view class="DayTitle">
			<span>近6个月明细</span>
			<view>
				<span>筛选</span>
				<image src="@/static/boc_select_gray.png" mode=""></image>
			</view>
		</view>
		
		<view v-for="(item,index) in datails" :key="index">
			<view class="ApplicationStatus-list">
				<view class="time">
					{{item.YearMonth}}
				</view>
				<view class="li" v-for="(sum,num) in item.list" :key="num+10">
					<view class="date">
						<view>
							<span>{{sum.Day}}</span>
							<p>{{sum.week}}</p>
						</view>
					</view>
					<view class="centent">
						<view class="centent-view">
							<view class="Left-View">
								<span>{{sum.title}}</span>
								<p>余额 {{sum.balance}}</p>
							</view>
							<view class="Right-View">
								<span>{{sum.username}}</span>
								<p>人民币元 <text :style="{color: sum.color ? '#e6596d':'#1e9474'}">{{sum.add}}</text></p>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	import AccountCardVue from '../../components/AccountCard.vue';
	import loanTitleVue from '../../components/loan-Title.vue';
	export default {
		data() {
			return {
				list:[{number:'6216 ****** 6429',SubNumber:'长城电子借记卡(I类账户)'}],
				TitleImage:"../../static/back_black.png",
				datails:[
					{
						YearMonth:'06月/2025',
						list:[
							{Day:'01',week:'周日',title:'贷款还款',balance:'45,084.39',username:'马文超',add:'-6,518.09',color:false},
						],
					},
					{
						YearMonth:'05月/2025',
						list:[
							{Day:'01',week:'周四',title:'贷款还款',balance:'51,602.48',username:'马文超',add:'-6,518.59',color:false},
						],
					},
					{
						YearMonth:'04月/2025',
						list:[
							
							{Day:'29',week:'周二',title:'网上快捷提现',balance:'58,121.08',username:'财务通-马文超',add:'1,185.00',color:true},
							{title:'跨行转账',balance:'56,936.08',username:'江满杭',add:'31,170.00'},
							{Day:'01',week:'周二',title:'贷款还款',balance:'25,766.08',username:'马文超',add:'-6,519.01',color:false},
						],
					},
					{
						YearMonth:'03月/2025',
						list:[
							{Day:'20',week:'周四',title:'结息',balance:'32,285.09',username:'马文超',add:'0.19',color:true},
							{Day:'01',week:'周六',title:'贷款还款',balance:'32,284.90',username:'马文超',add:'-6,519.50',color:false},
						],
					},
					{
						YearMonth:'02月/2025',
						list:[
							{Day:'01',week:'周六',title:'贷款还款',balance:'38,804.40',username:'马文超',add:'-6,512.50',color:false},
						],
					},
					{
						YearMonth:'01月/2025',
						list:[
							{Day:'25',week:'周六',title:'网上支付',balance:'45,316.96',username:'支付宝',add:'-114.80',color:false},
							{Day:'10',week:'周五',title:'网上快捷提现',balance:'45,431.76',username:'财务通-马文超',add:'1,700.00',color:true},
							{Day:'02',week:'周四',title:'贷款还款',balance:'43,731.76',username:'马文超',add:'-6.520.04',color:false},
							{Day:'01',week:'周三',title:'网上快捷提现',balance:'50,251.80',username:'财务通-马文超',add:'499.50',color:true},
							{title:'银联入账',balance:'49,752.30',username:'马文超',add:'29,970.03'},
						],
					},
					{
						YearMonth:'12月/2024',
						list:[
							{Day:'20',week:'周五',title:'结息',balance:'19,782.27',username:'马文超',add:'1.32',color:true},
							{Day:'02',week:'周一',title:'贷款还款',balance:'19,780.95',username:'马文超',add:'-6,016.33',color:false},
						],
					},
					{
						YearMonth:'11月/2024',
						list:[
							{Day:'30',week:'周六',title:'银联入账',balance:'25,797.28',username:'马文超',add:'13,801.28',color:true},
						],
					},
				],
				TopTitle:0
			};
		},
		components:{
			AccountCardVue,
			loanTitleVue
		},
		onPageScroll(TopTitle) {
			this.TopTitle = TopTitle.scrollTop
			
		}
	}
</script>

<style lang="scss">
	.accountDatails{
		width: 100vw;
		min-height: 100vh;
		background-color: #f4f4f4;
		.accountDatails-title{
			background-color: #fff;
		}
		.accountDatails-card{
			width: 95%;
			margin: 20rpx auto;
			border-radius: 10rpx;
			background-color: #fff;
		}
		.DayTitle{
			display: flex;
			align-content: center;
			justify-content: space-between;
			margin-bottom: 10rpx;
			padding:10rpx 30rpx;
			span{
				color: #6d6d6d;
				font-size: 25rpx;
			}
			view{
				display: flex;
				align-items: center;
				color: #dd1847;
				image{
					width: 30rpx;
					height: 30rpx;
				}
			}
		}
		.ApplicationStatus-list{
			.time{
				background-color: #f9f9f9;
				color: #888;
				font-size: 22rpx;
				padding:15rpx 20rpx;
				border-bottom: 1px solid #bdbdbd;
			}
			.li{
				display: flex;
				align-content: center;
				background-color: #f9f9f9;
				.date{
					color: #888;
					display: flex;
					flex-wrap: wrap;
					justify-content: center;
					align-items: center;
					view{
						min-width: 40rpx;
						padding: 20rpx;
						span{
							font-size: 35rpx;
							font-weight: bold;
						}
						p{
							text-align: center;
							width: 100%;
							font-size: 18rpx;
						}
					}
					
				}
				.centent{
					flex: 1;
					background-color: #fff;
					border-bottom: 1px solid #ddd;
					display: flex;
					align-items: center;
					.centent-view{
						width: 100%;
						font-size: 25rpx;
						padding: 15rpx;
						display: flex;
						justify-content: space-between;
						.Left-View{
							span{
								font-size: 28rpx;
							}
							p{
								margin-top: 5rpx;
								color:#6f6f6f;
							}
						}
						.Right-View{
							text-align: right;
							span{
								font-size: 25rpx;
							}
							p{
								margin-top: 5rpx;
								color:#6f6f6f;
								font-size: 30rpx;
								color: #000;
								text{
									padding-left:10rpx;
								}
							}
						}
					}
				}
			}
		}
	}
	
</style>
