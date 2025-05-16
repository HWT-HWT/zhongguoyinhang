<template>
	<view class="Loan-Datali-remaining">
		<view class="remaining-Title">
			<view class="Title">
				还款方式: <span>协议还款</span>
			</view>
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
				<span>{{item.Money[1]}}</span>
			</view>
		</view>
		<footVue></footVue>
	</view>
</template>

<script>
	import footVue from './foot.vue';
	export default {
		name:"remaining",
		data() {
			return {
				remainingListOne:[
					{id:1,date:'2025/04/03',Money:['应还款3,047.12','本金1,800.00|利息1,247.12']},
					{id:2,date:'2025/05/03',Money:['应还款3,036.12','本金1,800.00|利息1,241.64']},
					{id:3,date:'2025/06/03',Money:['应还款3,030.64','本金1,800.00|利息1,230.64']},
					{id:4,date:'2025/07/03',Money:['应还款3,025.16','本金1,800.00|利息1,225.16']},
					{id:5,date:'2025/08/03',Money:['应还款3,019.68','本金1,800.00|利息1,219.68']},
					{id:6,date:'2025/09/03',Money:['应还款3,014.20','本金1,800.00|利息1,214.20']},
					{id:7,date:'2025/10/03',Money:['应还款3,008.72','本金1,800.00|利息1,208.72']},
					{id:8,date:'2025/11/03',Money:['应还款3,003.24','本金1,800.00|利息1,203.24']},
					{id:9,date:'2025/12/03',Money:['应还款2,997.76','本金1,800.00|利息1,197.76']},
					{id:10,date:'2026/01/03',Money:['应还款2,992.28','本金1,800.00|利息1,192.28']},
					{id:11,date:'2026/02/03',Money:['应还款2,986.80','本金1,800.00|利息1,186.80']},
					{id:12,date:'2026/03/03',Money:['应还款2,981.32','本金1,800.00|利息1,181.32']},
					{id:13,date:'2026/03/17',Money:['应还款437,814.58','本金437,000.00|利息814.58']},
				],
				
				remainingList:[
					{id:1,date:'2025/04/03',Money:['应还款6,259.82','本金4,721.00|利息1,538.82']},
					{id:2,date:'2025/05/03',Money:['应还款6,254.34','本金4,721.00|利息1,533.34']},
					{id:3,date:'2025/06/03',Money:['应还款6,248.86','本金4,721.00|利息1,527.86']},
					{id:4,date:'2025/07/03',Money:['应还款6,243.38','本金4,721.00|利息1,522.38']},
					{id:5,date:'2025/08/03',Money:['应还款6,237.90','本金4,721.00|利息1,516.90']},
					{id:6,date:'2025/09/03',Money:['应还款6,232.42','本金4,721.00|利息1,511.42']},
					{id:7,date:'2025/10/03',Money:['应还款6,226.94','本金4,721.00|利息1,505.94']},
					{id:8,date:'2025/11/03',Money:['应还款6,221.46','本金4,721.00|利息1,500.46']},
					{id:9,date:'2025/12/03',Money:['应还款6,215.98','本金4,721.00|利息1,494.98']},
					{id:10,date:'2026/01/03',Money:['应还款6,210.50','本金4,721.00|利息1,489.50']},
					{id:11,date:'2026/02/03',Money:['应还款6,205.02','本金4,721.00|利息1,484.02']},
					{id:12,date:'2026/03/03',Money:['应还款6,199.54','本金4,721.00|利息1,478.54']},
					{id:13,date:'2026/03/13',Money:['应还款435,579.58','本金434,765.00|利息814.58']},
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

<style lang="scss">
	.Loan-Datali-remaining{
		width: 100%;
		background-color: #fff;
		.remaining-Title{
			font-size: 28rpx;
			.Title{
				width: 100%;
				background-color: #f5f9fe;
				padding: 20rpx;
				span{
					font-weight: bold;
					margin-left: 10rpx;
				}
			}
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