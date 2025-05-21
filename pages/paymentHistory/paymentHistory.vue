<template>
	<view class="payment-history">
		<view class="Loan-Datali-Tab">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' :RightMax='1' :isText='false' Color="#000">
				还款记录 
			</backtaberVue>
		</view>
		<view class="Loan-Datali-Tabs">
		 	<z-tabs ref="tabs" :list="tabListOne" :current="current" active-color="#e82e4a" @change="tabsChange" />
		</view>
		<remainingVue v-if="current === 0" :IsTrue='IsTrue'></remainingVue>
		<historyVue v-if="current === 1"  :IsTrue='IsTrue'></historyVue>
		<overdueVue v-if="current === 2" :IsTrue='IsTrue'></overdueVue>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	import backtaberVue from '../../components/backtaber.vue'
	import remainingVue from '../../components/remaining.vue';
	import historyVue from '../../components/history.vue';
	import overdueVue from '../../components/overdue.vue';
	export default {
		data() {
			return {
				TitleImage:"../../static/back_black.png",
				rigthIcon:['../../static/boc_folder_title_service.png'],
				tabList: ['剩余','历史','逾期'],
				tabListOne: ['待还款','已还款','逾期待还款'],
				current: 0,
				IsTrue:''
				
			};
		},
		components:{
			occupyVue,
			backtaberVue,
			remainingVue,
			historyVue,
			overdueVue
		},
		methods:{
			 tabsChange(index) {
				this.current = index;
			},
		},
		props:{
			
		},
		onLoad(query) {
			console.log(query.isTrue);
			this.IsTrue = query.isTrue == 2 ? false : true
			console.log(this.IsTrue);
		}
	}
</script>

<style lang="scss" scoped>
	.payment-history{
		width: 100vw;
		height: 100vh;
		background-color: #f4f4f4;
		.Loan-Datali-Tab{
			width: 100%;
			background-color: #fff;
			// position: fixed;
			// top: 0;
		}
		.Loan-Datali-Tabs{
			padding:0 50rpx;
			margin: 0 auto;
			background-color: #fff;
		}
		
	}
</style>
