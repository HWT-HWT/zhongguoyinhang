<template>
	<view class="AccountOverview-card">
		<view class="card-icon" v-for="(item,index) in list" :key="index">
			<image src="@/static/AccountOverview-bg-2.png" mode=""></image>
			<view class="card-number">
				<p>{{item.number}}</p>
				<span>{{item.SubNumber}}</span>
			</view>
			<text v-if="btn">去关联</text>
		</view>
	</view>
</template>

<script>
	export default {
		name:"AccountCard",
		data() {
			return {
				
			};
		},
		props:{
			list:{
				type:[Array,Object]
			},
			btn:{
				type:Boolean,
				default:true
			}
		}
	}
</script>

<style lang="scss" scoped>
	.AccountOverview-card{
		width: 90%;
		margin: 0 auto;
		margin-top: 20rpx;
		// background-color: #000;
		.card-icon{
			padding: 30rpx;
			display: flex;
			align-items: center;
			background-color: #fff;
			margin-top: 20rpx;
			border-radius: 20rpx;
			image{
				width: 120rpx;
				height: 80rpx;
			}
			.card-number{
				flex: 1;
				margin-left: 20rpx;
				p{
					font-size: 30rpx;
					font-weight: bold;
				}
				span{
					font-size: 23rpx;
				}
			}
			text{
				font-size: 25rpx;
				color:#376fd3 ;
			}
		}
		.money{
			padding: 30rpx;
			background-color: #fbf8f1;
			display: flex;
			justify-content: space-between;
			font-size: 25rpx;
			color: #666665;
			span{
				font-weight: bold;
				text{
					margin-left: 10rpx;
					color: #000;
				}
			}
			
		}
		.card-list{
			display: flex;
			align-items: center;
			justify-content: space-between;
			padding: 20rpx 0;
			.listView{
				font-size: 28rpx;
				width: 33%;
				border-right:1px solid #ddd;
				text-align: center;
			}
		}
	}
</style>