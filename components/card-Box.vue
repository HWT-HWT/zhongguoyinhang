<template>
	<view class="MyAccount-Card">
		 <view class="Card-content">
		 	<image src="@/static/card-image-1.png" mode=""></image>
			<view class="content-text">
				<span>{{cardName}}</span>
				<p>{{subName}}</p>
			</view>
		 </view>
		 <view class="Card-Money">
		 	<view class="span">账面余额 </view>
			<text>人民币元 <span>{{!Eye ? '***' :  money}}</span></text>
		 </view>
		 <view class="card-Btn">
		 	<view class="btn" v-for="(item,index) in listBtn" :key="index" :style="{borderRight:index+1 === listBtn.length ? 'none' :'1px solid #ddd' }" @click="Next(index)">
		 		{{item}}
		 	</view>
		 </view>
	</view>
</template>

<script>
	export default {
		name:"card-Box",
		data() {
			return {
				
			};
		},
		props:{
			listBtn:{
				type:Array
			},
			cardName:{
				type:String
			},
			subName:{
				type:String
			},
			money:{
				type:String
			},
			id:{
				type:Number
			},
			Eye:{
				type:Boolean
			}
		},
		methods:{
			Next(index){
				this.$emit('Next',{index:index,id:this.$props.id})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.MyAccount-Card{
		width: 100%;
		margin: 0 auto;
		box-shadow: 0 0 10rpx rgba(0, 0, 0, 0.1);
		margin-top: 20rpx;
		border-radius: 20rpx;
		.Card-content{
			width: 90%;
			display: flex;
			margin: 0 auto;
			align-items: center;
			padding: 30rpx 0;
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
		.Card-Money{
			margin: 0 auto;
			display: flex;
			align-items: center;
			justify-content: space-between;
			padding-bottom: 30rpx;
			padding-top: 20rpx;
			font-size: 30rpx;
			background-color: #f3ead9;
			padding: 40rpx;
			color: #666;
			.span{
				display: flex;
				align-items: center;
				color: #666;
			}
			span{
				color: #000;
				margin-left: 10rpx;
			}
		}
		.card-Btn{
			width: 100%;
			display: flex;
			align-items: center;
			.btn{
				width: 33%;
				margin: 30rpx 0;
				border-right: 1px solid #666;
				text-align: center;
				font-size: 30rpx;
			}
		}
	}
</style>