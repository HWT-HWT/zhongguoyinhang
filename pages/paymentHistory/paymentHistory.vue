<template>
	<view class="payment-history">
		<view class="Loan-Datali-Tab">
			<loanTitleVue :name="'还款记录'" :TitleImage='TitleImage' :rigthIcon='rigthIcon' :Scollor="TopTitle"></loanTitleVue>
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
	import loanTitleVue from '../../components/loan-Title.vue';
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
				IsTrue:'',
				TopTitle:''
			};
		},
		components:{
			loanTitleVue,
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
		},
		onPageScroll(TopTitle) {
			this.TopTitle = TopTitle.scrollTop
		}
	}
</script>

<style lang="scss" scoped>
	.payment-history{
		width: 100vw;
		min-height: 100vh;
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
