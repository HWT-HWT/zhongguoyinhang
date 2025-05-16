<template>
	<view class="history">
		<view class="remaining-Title">
			<view class="SubText">
				单位: 人民币元 
			</view>
		</view>
		<view class="remaining-ListView" v-for="(item,index) in IsTrue ? remainingList : remainingListOne" :key="index">
			<view class="num">
				{{item.id}}
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
					{id:1,date:'2025/03/03',Money:['已还款3,047.12','1,800.00|利息1,247.12',]},
					{id:2,date:'2025/02/03',Money:['已还款3,052.60','1,800.00|利息1,252.60',]},
					{id:3,date:'2025/01/03',Money:['已还款3,058.08','1,800.00|利息1,258.08',]},
					{id:4,date:'2024/12/03',Money:['已还款3,063.56','1,800.00|利息1,263.56',]},
					{id:5,date:'2024/11/03',Money:['已还款3,069.04','1,800.00|利息1,269.04',]},
					{id:6,date:'2024/10/03',Money:['已还款3,074.52','1,800.00|利息1,274.52',]},
					{id:7,date:'2024/09/03',Money:['已还款3,080.10','1,800.00|利息1,280.10',]},
					{id:8,date:'2024/08/03',Money:['已还款3,085.48','1,800.00|利息1,285.48',]},
					{id:9,date:'2024/07/03',Money:['已还款3,090.68','1,800.00|利息1,290.68',]},
					{id:10,date:'2024/06/03',Money:['已还款3,069.16','1,800.00|利息1,296.60',]},
					{id:11,date:'2024/05/03',Money:['已还款3,101.64','1,800.00|利息1,301.64',]},
					{id:12,date:'2024/04/03',Money:['已还款3,107.12','1,800.00|利息1,307.12',]},
					{id:13,date:'2024/03/03',Money:['已还款3,188.68','1,800.00|利息1,388.18',]},
					{id:14,date:'2024/02/03',Money:['已还款3,193.66','1,800.00|利息1,393.66',]},
					{id:15,date:'2024/01/03',Money:['已还款3,199.14','1,800.00|利息1,399.14',]},
					{id:16,date:'2023/12/03',Money:['已还款3,204.62','1,800.00|利息1,404.62',]},
					{id:17,date:'2023/11/03',Money:['已还款3,210.10','1,800.00|利息1,410.10',]},
					{id:18,date:'2023/10/03',Money:['已还款3,215.58','1,800.00|利息1,415.58',]},
					{id:19,date:'2023/09/03',Money:['已还款3,221.06','1,800.00|利息1,421.06',]},
					{id:20,date:'2023/08/03',Money:['已还款3,226.54','1,800.00|利息1,426.54',]},
					{id:21,date:'2023/07/03',Money:['已还款3,232.02','1,800.00|利息1,432.02',]},
					{id:22,date:'2023/06/03',Money:['已还款3,237.50','1,800.00|利息1,437.50',]},
					{id:23,date:'2023/05/03',Money:['已还款4,054.28','1,800.00|利息2,254.28',]},
				],
				
				remainingList:[
					{id:1,date:'2025/03/03',Money:['已还款6,268.12','4,721.00|利息1,547.12',]},
					{id:2,date:'2025/02/03',Money:['已还款6,273.60','4,721.00|利息1,552.60',]},
					{id:3,date:'2025/01/03',Money:['已还款6,279.08','4,721.00|利息1,558.08',]},
					{id:4,date:'2024/12/03',Money:['已还款6,284.56','4,721.00|利息1,563.56',]},
					{id:5,date:'2024/11/03',Money:['已还款6,290.04','4,721.00|利息1,569.04',]},
					{id:6,date:'2024/10/03',Money:['已还款6,295.52','4,721.00|利息1,574.52',]},
					{id:7,date:'2024/09/03',Money:['已还款6,301.10','4,721.00|利息1,580.10',]},
					{id:8,date:'2024/08/03',Money:['已还款6,306.48','4,721.00|利息1,585.48',]},
					{id:9,date:'2024/07/03',Money:['已还款6,311.68','4,721.00|利息1,590.68',]},
					{id:10,date:'2024/06/03',Money:['已还款6,317.60','4,721.00|利息1,596.60',]},
					{id:11,date:'2024/05/03',Money:['已还款6,322.64','4,721.00|利息1,601.64',]},
					{id:12,date:'2024/04/03',Money:['已还款6,328.12','4,721.00|利息1,607.12',]},
					{id:13,date:'2024/03/03',Money:['已还款6,409.68','4,721.00|利息1,688.68',]},
					{id:14,date:'2024/02/03',Money:['已还款6,414.66','4,721.00|利息1,693.66',]},
					{id:15,date:'2024/01/03',Money:['已还款6,420.14','4,721.00|利息1,699.14',]},
					{id:16,date:'2023/12/03',Money:['已还款6,425.62','4,721.00|利息1,704.62',]},
					{id:17,date:'2023/11/03',Money:['已还款6,431.10','4,721.00|利息1,710.10',]},
					{id:18,date:'2023/10/03',Money:['已还款6,436.58','4,721.00|利息1,715.58',]},
					{id:19,date:'2023/09/03',Money:['已还款6,442.06','4,721.00|利息1,721.06',]},
					{id:20,date:'2023/08/03',Money:['已还款6,435.39','4,721.00|利息1,714.39',]},
					{id:21,date:'2023/07/03',Money:['已还款6,440.87','4,721.00|利息1,719.87',]},
					{id:22,date:'2023/06/03',Money:['已还款6,446.35','4,721.00|利息1,725.35',]},
					{id:23,date:'2023/05/03',Money:['已还款7,426.12','4,721.00|利息2,705.12',]},
				]
			};
		},
		components:{
			footVue
		},
		props:{
			IsTrue:{
				type:Boolean,
			}
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