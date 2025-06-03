<template>
	<view class="history">
		<view class="remaining-Title">
			<view class="SubText">
				单位: 人民币元 
			</view>
		</view>
		<view class="remaining-ListView"  v-for="(item,index) in !IsTrue ? remainingListOne :  remainingList" :key="index">
			<view class="num">
				{{index+1}}  
			</view>
			<view class="date">
				{{item.date}}
			</view>
			<view class="Money">
				<p>{{item.Money[0]}}</p>
				<span>本金{{item.Money[1]}}</span>
			</view>
		</view>
		
		<footVue></footVue>
		
	</view>
</template>

<script>
	import footVue from './foot.vue';
	export default {
		name:"history",
		data() {
			return {
				
				remainingListOne:[
					{id:1,date:'2025/05/11',Money:['已还款567.47','0.00|利息567.47',]},
					{id:2,date:'2025/04/29',Money:['已还款588.51','0.00|利息588.51',]},
					{id:3,date:'2025/02/11',Money:['已还款531.03','0.00|利息531.03',]},
					{id:4,date:'2024/01/11',Money:['已还款585.15','0.00|利息585.15',]},
					{id:5,date:'2024/11/03',Money:['已还款1,114.44','0.00|利息1,114.44',]},
				],
				
				remainingList:[
					{date:'2025/06/01',Money:['应还款6,518.09','本金4,000.00|利息2,518.09']},
					{date:'2025/05/01',Money:['已还款6,518.59','4,000.00|利息2,518.59',]},
					{date:'2025/04/01',Money:['已还款6,519.01','4,000.00|利息2,519.01',]},
					{date:'2025/03/01',Money:['已还款6,519.50','4,000.00|利息2,519.50',]},
					{date:'2025/02/01',Money:['已还款6,512.56','4,000.00|利息2,512.56',]},
					{date:'2025/01/02',Money:['已还款6,520.04','4,000.00|利息2,520.04',]},
				],
				index:1
			};
		},
		components:{
			footVue
		},
		props:{
			IsTrue:{
				type:Boolean,
			}
		},
		onLoad(parma){
			console.log(parma);
			this.index = parma.id
		}
	}
</script>

<style lang="scss" scoped>
	.history{
		width: 100vw;
		.remaining-Title{
			font-size: 28rpx;
			.SubText{
				background-color: #f4f4f4;
				padding: 10rpx 20rpx;
				text-align: right;
			}
		}
		.remaining-ListView{
			display: flex;
			align-items: center;
			justify-content: space-between;
			background-color: #fff;
			padding: 20rpx;
			border-bottom: 1px solid #ddd;
			.num{
				width: 50rpx;
				height: 50rpx;
				font-size: 25rpx;
				background-color: #f4f4f4;
				border-radius: 50rpx;
				display: flex;
				align-items: center;
				justify-content: center;
			}
			.date{
				font-weight: bold;
				font-size: 28rpx;
			}
			.Money{
				width: 55%;
				text-align: right;
				p{
					font-size: 30rpx;
					font-weight: bold;
				}
				span{
					font-size: 25rpx;
				}
			}
		}
	}
</style>