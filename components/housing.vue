<template>
	<view class="housing">
		<loanTitleVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' :name='name'></loanTitleVue>
		<view class="loan-Setting">
			<ListViewVue :listTitle="loanSetting" FontSize="25rpx" sizi='60rpx' width="25%" Pad='30rpx 0'></ListViewVue>
		</view>
		<view class="housing-guide">
			<titleVue LFontSize="38">
				<template #left>
					贷款指南
				</template>
			</titleVue>
			<view class="guide-btn">
				<view class="btn" v-for="(item,index) in guideList" :key="index">
					{{item}}
				</view>
			</view>
			<view class="guide-listView">
				<p class="FW">Q:什么是个人住房贷款?</p>
				<p><span class="FW">A:</span>个人住房贷款是我行为符合条件的借款人提供的用于购买住房的商业性贷款。</p>
			</view>
			<view class="guide-listView" :style="{border:'none'}">
				<p  class="FW">Q:个人住房贷款的期限是多长</p>
				<p><span class="FW">A:</span>目前个人住房的贷款期限最长为30年,若相关法律法规、监管部门或国家政策规定有更新规定的,则从其规定。</p>
			</view>
		</view>
	</view>
</template>

<script>
	import ListViewVue from './ListView.vue';
	import backtaberVue from '../components/backtaber.vue';
	import occupyVue from '../components/occupy.vue';
	import titleVue from './titleVue.vue';
	import loanTitleVue from './loan-Title.vue';
	export default {
		name:"housing",
		data() {
			return {
				TitleImage:"../../static/back_black.png",
				rigthIcon:['../../static/boc_folder_title_service.png','../../static/icon_share_black.png'],
				loanSetting:[
					{name:'还款管家',icon:'../../static/housing-icon-1.png'},
					{name:'房贷利率调整',icon:'../../static/housing-icon-2.png'},
					{name:'房产估值',icon:'../../static/housing-icon-3.png'},
					{name:'贷款计算器',icon:'../../static/housing-icon-4.png'},
					{name:'全国基金查询',icon:'../../static/housing-icon-5.png'},
					{name:'征信查询',icon:'../../static/housing-icon-6.png'},
				],
				guideList:['政策','办理','更多']
			};
		},
		components:{
			ListViewVue,
			backtaberVue,
			occupyVue,
			titleVue,
			loanTitleVue
		},
		props:{
			name:{
				type:String
			}
		}
	}
</script>

<style lang="scss" scoped> 
	.housing{
		width: 100%;
		padding-bottom: 100rpx;
		background: url('@/static/consumption-bg-2.png')no-repeat;
		background-size: 100% 400rpx;
		background-color: #fff;
		.loan-Setting{
			width: 90%;
			margin: 0 auto;
			margin-top: 280rpx;
		}
		.housing-guide{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			.guide-btn{
				display: flex;
				margin-bottom: 20rpx;
				.btn{
					padding:10rpx 40rpx;
					background-color: #f5eadd;
					border-radius: 10rpx;
					color: #7d532a;
					margin: 0 10rpx;
					font-size: 28rpx;
				}
			}
			.guide-listView{
				background-color: #f8f8f8;
				padding: 30rpx ;
				line-height: 50rpx;
				border-radius: 10rpx;
				border-bottom: 1px dashed #ddd;
				font-size: 28rpx;
				.FW{
					font-weight: bold;
				}
			}
		}
	}
</style>