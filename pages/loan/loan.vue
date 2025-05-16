<template>
	<view class="loan">
		<consumptionVue v-if="TaberIndex===0" :TopTitle='scrollTop' :name='Taber[TaberIndex]' ></consumptionVue>
		<housingVue v-if="TaberIndex===1" :TopTitle='scrollTop' :name='Taber[TaberIndex]'></housingVue>
		<operateVue  v-if="TaberIndex===2" :TopTitle='scrollTop' :name='Taber[TaberIndex]'></operateVue>
		<assistLearningVue v-if="TaberIndex===3" :TopTitle='scrollTop' :name='Taber[TaberIndex]'></assistLearningVue>
		<MyLoanVue  v-if="TaberIndex===4" :TopTitle='scrollTop' :name='Taber[TaberIndex]'></MyLoanVue>
		<view class="loan-taber">
			<view class="Taber-List " :class="{'Taber-Select':TaberIndex===index}" v-for="(item,index) in Taber " :key="index" @click="Switch(index)">
				{{item}}
			</view>
		</view>
	</view>
</template>

<script>
	import backtaberVue from '../../components/backtaber.vue';
	import occupyVue from '../../components/occupy.vue';
	import consumptionVue from '../../components/consumption.vue';
	import housingVue from '../../components/housing.vue';
	import operateVue from '../../components/operate.vue';
	import assistLearningVue from '../../components/assist-Learning.vue';
	import MyLoanVue from '../../components/MyLoan.vue';
	export default {
		data() {
			return {
				TitleImage:"../../static/back_black.png",
				rigthIcon:['../../static/boc_folder_title_service.png','../../static/icon_share_black.png'],
				Taber:['消费','住房','经营','助学','我的贷款'],
				TaberIndex:0,
				scrollTop:0
			};
		},
		components:{
			backtaberVue,
			occupyVue,
			consumptionVue,
			housingVue,
			operateVue,
			assistLearningVue,
			MyLoanVue
		},
		methods:{
			Switch(index){
				this.TaberIndex = index
			}
		},
		onPageScroll(Scroll) {
			this.scrollTop =  Scroll.scrollTop
		}
	}
</script>

<style lang="scss">
	.loan{
		width: 100vw;
		background-color: #f7f7f7;
		.loan-taber{
			width: 100%;
			display: flex;
			justify-content: space-between;
			background-color: #fff;
			position: fixed;
			bottom: 0;
			padding: 10rpx;
			box-shadow: 0 0 10rpx 1rpx rgba(0, 0, 0, .1);
			.Taber-List{
				font-size: 30rpx;
				padding: 15rpx;
				font-weight: bold;
				color: #555;
			}
			.Taber-Select{
				border-bottom:2px solid #dc0739;
				color: #000;
			}
		}
	}
</style>
