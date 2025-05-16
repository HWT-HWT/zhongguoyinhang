<template>
	<view class="index-listTitle" :style="{'background':BgColor}">
		<view class="listTitle" v-for="(item,index) in listTitle" :key="index" :style="{'padding' :Pad, width:width}" @click="onclick(index)">
			<image v-if="item.icon" :src="item.icon" :style="{'width':sizi,'height':sizi}" mode=""></image>
			<span v-else>{{item.num}}</span>
			<view class="listTitle-lade" :style="{'fontSize':FontSize}">{{item.name}}</view>
		</view>
	</view>
</template>

<script>
	import {gologin} from '@/unit/login.js'
	export default {
		name:"ListView",
		data() {
			return {
				
			};
		},
		props:{
			listTitle:{
				type:[Object,Array]
			},
			sizi:{
				type:String,
				default:'70rpx'
			},
			BgColor:{
				type:String,
				default:'none'
			},
			FontSize:{
				type: String,
				default:'28rpx'
			},
			Pad:{
				type: String,
				default:'10rpx 0'
			},
			width:{
				type: String,
				default:'20%'
			},
			index:{
				type:Number,
			},
			url:{
				type:String
			}
		},
		methods:{
			onclick(index){
				this.$emit('ClickNext',index)
			}
		}
	}
</script>

<style lang="scss" scoped>
	.index-listTitle{
		display: flex;
		width: 100%;
		margin: 0 auto;
		// justify-content: space-between;
		flex-wrap: wrap;
		border-radius: 30rpx;
		font-size: 35rpx;
		.listTitle{
			width: 20%;
			display: flex;
			flex-wrap: wrap;
			align-items: center;
			justify-content: center;
			margin-bottom: 0rpx;
			.listTitle-lade{
				font-size: 30rpx;
				width: 100%;
				text-align: center;
				margin-top: 10rpx;
				height: 20rpx;
				padding: 0 5rpx;
			}
		}
	}
</style>