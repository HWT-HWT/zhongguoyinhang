<template>
	<view>
		<view class="scroll-view">
			<view class="Optimal-title-btn">
				<view class="Optimal-btn" v-for="(item,index) in list" :key="index">
					{{item}}
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"scroll-btn",
		data() {
			return {
				
			};
		},
		props:{
			list:{
				type:Array
			}
		}
	}
</script>

<style lang="scss" scoped>
	.scroll-view{
		width: 100%;
		margin: 30rpx auto;
		display: flex;
		justify-content: space-between;
		.Optimal-title-btn{
			width: 100%;
			padding-left: 10rpx;
			display: flex;
			align-items: center;
			.Optimal-btn{
				margin-right: 20rpx;
				height: 45rpx;
				padding: 0 20rpx;
				border-radius: 40rpx;
				font-size: 30rpx;
				background-color: #fef5f6;
				color: #333;
				display: flex; 	
				align-items: center;
			}
			.Optimal-btn:hover{
				color: #cb0c35;
				font-weight: bold;
			}
		}
	}
</style>