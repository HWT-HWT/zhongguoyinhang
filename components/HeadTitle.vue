<template>
	<view class="index-title">
		<view class="login" v-if="Icon" @click="GoLogin(isTrue)">
			<image :src="Icon" mode="" :style="{width:IconSize[0],height:IconSize[1]}"></image>
			<p  :style="{color:TextColor}"><slot></slot></p>
		</view>
		<view class="title-input" :style="{background:BgColor}">
			<image src="@/static/boc_finance_search.png" mode=""></image>
			<input type="text" placeholder="请输入" />
			<image src="@/static/microphone.png" mode=""></image>
		</view>
		<view class="title-icon" v-for="(item,index) in menu" :key="index">
			<image :src="item.image" mode=""></image>
			<p :style="{color:TextColor}">{{item.name}}</p>
		</view>
	</view>
</template>

<script>
	export default {
		name:"HeadTitle",
		data() {
			return {
				BgColor:'#f4f4f4',
				token:''
			};
		},
		props:{
			menu:{
				type:[Object,Array]
			},
			Icon:{
				type:String
			},
			TextColor:{
				type:String
			},
			IconSize:{
				type:[Array],
				default:function (){
					return ['40rpx','40rpx']
				}
			},
			isTrue:{
				type:Boolean,
				default:true
			}
		},
		methods:{
			GoLogin(isTrue){
				if(isTrue){
					uni.navigateTo({
						url:'/pages/gesture/gesture'
					})
				}else{
					if(uni.getStorageSync('account')){
						uni.removeStorageSync('account')
						uni.navigateTo({
							url:'/pages/gesture/gesture'
						})
					}else{
						uni.navigateTo({
							url:'/pages/gesture/gesture'
						})
					}
				}
			}
		},
	}
</script>

<style lang="scss" scoped>
	.index-title{
		padding:0 20rpx;
		display: flex;
		align-items: center;
		justify-content: space-between;
		font-size: 28rpx;
		p{
			text-align: center;
			width: 100%;
			margin-top: 5rpx;
		}
		.login{
			color: #fff;
			display: flex;
			flex-wrap: wrap;
			justify-content: center;
			margin-right: 20rpx;
			image{
				width: 40rpx;
				height: 40rpx;
			}
		}
		.title-input{
			flex: 1;
			height: 70rpx;
			border-radius: 50rpx;
			background-color: #fff;
			display: flex;
			align-items: center;
			justify-content: center;
			padding:0 20rpx;
			image{
				width: 35rpx;
				height: 35rpx;
			}
			input{
				flex: 1;
				font-size: 28rpx;
				margin: 0 20rpx;
			}
		}
		.title-icon{
			color: #fff;
			display: flex;
			flex-wrap: wrap;
			justify-content: center;
			margin-left: 20rpx;
			image{
				width: 40rpx;
				height: 40rpx;
			}
			p{
				text-align: center;
				width: 100%;
			}
		}
	}
</style>