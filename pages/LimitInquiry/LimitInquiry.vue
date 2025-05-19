<template>
	<view class="Limit-inquiry">
		<view class="Transaction-details-title">
			<loanTitleVue :TitleImage='TitleImage' :name='"额度查询"' ></loanTitleVue>
		</view>
		<view class="Transaction-details-listView" v-for="(item,index) in LimitInquiryList" :key="index"> 
			<view class="title">
				{{item.date}}
			</view>
			<view class="ListView">
				<view class="Date">
					<p>{{item.MiniDate}}</p>
					<span>{{item.week}}</span>
				</view>
				<view class="Datali">
					<view class="Datali-Row">
						<p>{{item.title}}</p>
					</view>
					<view class="Datali-Row">
						<p class="TextAlien">{{item.Money}}</p>
					</view>
				</view>
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
				LimitInquiryList:[
					{date:'11月/2027',MiniDate:'08',week:'周一',title:'随心智贷',Money:'人民币元 200,000.00'},
					{date:'10月/2034',MiniDate:'25',week:'周三',title:'中银E贷·经营贷',Money:'人民币元 900,000.00'},
				]
			};
		},
		components:{
			loanTitleVue
		}
	}
</script>

<style lang="scss">
	.Limit-inquiry{
		width: 100vw;
		height: 100vh;
		background-color: #f4f4f4;
		.Transaction-details-title{
			background-color: #fff;
			font-weight: bold;
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
					color: #999;
					p{
						font-size: 40rpx;
						font-weight: bold;
					}
					span{
						width: 100%;
						font-size: 20rpx;
					}
				}
				.Datali{
					flex: 1;
					padding: 20rpx;
					background-color: #fff;
					line-height: 50rpx;
					.Datali-Row{
						padding: 0 20rpx;
						p{
							font-size: 30rpx;
						}
						.TextAlien{
							text-align: right;
							font-size: 32rpx;
							font-weight: bold;
						}
					}
					
				}
				
			}
		}
	}
</style>
