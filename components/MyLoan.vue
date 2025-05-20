<template>
	<view class="MyLoan">
		<view class="MyLoan-title">
			<loanTitleVue :name="name" :TitleImage='TitleImage' :rigthIcon='rigthIcon' :Scollor="TopTitle"></loanTitleVue>
		</view>
		<view class="MyLoan-Notlogin" v-if="false">
			<view class="btn">
				登录查看
			</view>
		</view>
		<view class="MyLoan-login">
			<view class="btn">
				<view class="p" @click="ClickBtn">
					贷款本金总额月(人民币) 
					<image src="../static/boc_finance_eye_open.png" mode="" v-if="Eye"></image>
					<image src="../static/boc_finance_eye_close.png" mode="" v-else></image>
				</view>
				<span>{{Eye ? '1,100,000.00' :'******' }}</span>
			</view>
		</view>
		
		<view class="MyLoan-ListView" v-for="(item,index) in Eye ? MyLoanListView : MyLoanListViewFalse" :key="index" >
			<view class="ListView-Text" @click="GoNext(index)">
				<view class="ListView-title">
					<p>{{item.title}}</p>
					<!-- <p class="SubTitle" v-if="item.isTrue" >贷款余额(人民币元)</p>
					<p class="isTrue" v-if="item.isTrue" >{{Eye ? '458,600.00' :'******' }}</p> -->
				</view>
				<view class="ListView-content" v-for="(sum,num) in item.list" :key="num">
					<span>{{sum.name}}</span> <p>{{sum.num}}</p>
				</view>
			</view>
			
			<view class="ListView-btn">
				<view class="btn" v-for="(sum,num) in item.btn" :key="num" :style="{borderRight: num+1 === item.btn.length ? 'none' : '1px solid #ccc'}" @click="ViewBtn(item.id,num)">
					{{sum}}
				</view>
			</view>
		</view>
		
		<view class="MyLoan-service">
			<titleVue LFontSize="38">
				<template #left>
						贷款服务
				</template>
			</titleVue>
			<ListViewVue :listTitle="ServiceList" FontSize="25rpx" sizi='60rpx' width="25%" Pad='30rpx 0' BgColor="#fff" @ClickNext="GO"></ListViewVue>
		</view>
		<view class="loan-Setting">
			<titleVue LFontSize="38" RColor="#888">
				<template #left>
					贷款小工具
				</template>
			</titleVue>
			<ListViewVue :listTitle="loanSetting" FontSize="25rpx" sizi='60rpx' width="25%" Pad='30rpx 0' BgColor="#fff" @ClickNext='ClickNext'></ListViewVue>
		</view>
		
	</view>
</template>

<script>
	import loanTitleVue from './loan-Title.vue';
	import titleVue from './titleVue.vue';
	import ListViewVue from './ListView.vue';
	export default {
		name:"MyLoan",
		data() {
			return {
				TitleImage:"../../static/back_black.png",
				rigthIcon:['../../static/boc_folder_title_service.png','../../static/icon_share_black.png'],
				ServiceList:[
					{name:'贷款资金转出',icon:'../../static/MyLoan-icon-1.png'},
					{name:'在线签约',icon:'../../static/MyLoan-icon-2.png'},
					{name:'贷款资料上传',icon:'../../static/MyLoan-icon-3.png'},
					{name:'申请进度查询',icon:'../../static/MyLoan-icon-4.png'},
					{name:'贷款记录',icon:'../../static/MyLoan-icon-5.png'},
					{name:'房贷利率调整',icon:'../../static/MyLoan-icon-6.png'},
					{name:'LPR利率转换',icon:'../../static/MyLoan-icon-7.png'},
					{name:'还款管家',icon:'../../static/MyLoan-icon-8.png'},
					{name:'已结清贷款',icon:'../../static/MyLoan-icon-9.png'},
				],
				loanSetting:[
					{name:'贷款计算器',icon:'../../static/loan-setting-6.png'},
					{name:'征信查询',icon:'../../static/loan-setting-5.png'},
					{name:'额度查询',icon:'../../static/loan-setting-7.png'},
					{name:'在线签约',icon:'../../static/loan-setting-2.png'},
					{name:'交易流水打印',icon:'../../static/MyLoan-icon-5.png'},
					{name:'房产估值',icon:'../../static/operate-icon-6.png'},
				],
				MyLoanListView:[
					{	
						id:2,
						title:'随心智贷',
						list:[
							{name:'贷款金额',num:'人民币元 200,000.00'},
							{name:'可用额度',num:'人民币元 0.00'},
							{name:'贷款到期日',num:'2027/11/08'},
						],
						isTrue:true,
						btn:['还款计划','额度详情']
					},
					{
						id:1,
						title:'中银E贷·经营贷(惠如愿·E抵贷)',
						list:[
							{name:'总额度',num:'人民币元 900,000.00'},
							{name:'可用额度',num:'人民币元 0.00'},
							{name:'额度到期日',num:'2034/10/25'}
						],
						btn:['还款','额度详情']
					}
				],
				MyLoanListViewFalse:[
					{
						id:2,
						title:'随心智贷',
						list:[
							{name:'贷款金额',num:'******'},
							{name:'贷款到期日',num:'******'},
							{name:'贷款执行利率',num:'******'}
						],
						isTrue:true,
						btn:['还款计划','额度详情']
					},
					{	
						id:1,
						title:'中银E贷·经营贷(惠如愿·E抵贷)',
						list:[
							{name:'总额度',num:'******'},
							{name:'可用额度',num:'******'},
							{name:'额度到期日',num:'******'}
						],
						btn:['还款','额度详情']
					}
					
				],
				Eye:false,
				CreditA:{
					TotalBalance:'900,000.00',
					Money:'900,000.00',
					remaining:'0.00',
					Credit:[
						{name:'还款账户',text:'6216 ****** 6429',menu:'更改'},
						{name:'还款日',text:'每月05日'},
						{name:'年利率',text:'3.55%起'},
						{name:'额度到期日',text:'2034/10/25'},
						{name:'贷款额度号',text:'PF355470000046878744084'},
						{name:'额度状态',text:'生效'},
						{name:'贷款机构名称',text:'中国银行广州大岭支行'},
						{name:'贷款机构地址',text:'广州市南沙区江南路110号首层、二层'},
						{name:'贷款机构电话',text:'02084987481'},
					],
				},
				CreditB:{
					TotalBalance:'200,000.00',
					Money:'200,000.00',
					remaining:'0.00',
					Credit:[
						{name:'还款账户',text:'6216 ****** 6429',menu:'更改'},
						{name:'还款日',text:'每月11日'},
						{name:'年利率(单利)',text:'3.4%'},
						{name:'额度到期日',text:'2027/11/08'},
						{name:'贷款额度号',text:'PF533850000047334650473'},
						{name:'额度状态',text:'生效'},
						{name:'贷款机构名称',text:'中国银行广州大岭支行'},
						{name:'贷款机构地址',text:'广州市南沙区江南路110号首层、二层'},
						{name:'贷款机构电话',text:'02084987481'},
					],
				},
				
				
			};
		},
		props:{
			name:{
				type:String
			},
			TopTitle:{
				type:Number
			}
		},
		components:{
			loanTitleVue,
			titleVue,
			ListViewVue
		},
		methods:{
			ViewBtn(id,index){
				console.log(id);
				if(id === 1){
					// index === 0 ? uni.navigateTo({
					// 	url:'/pages/drawMoney/drawMoney'
					// }) :''
					uni.setStorageSync('Credit',this.CreditA)
					
					index === 0 ? uni.navigateTo({
						url:'/pages/Repayment/Repayment'
					}) :''
					index === 1 ? uni.navigateTo({
						url:'/pages/CreditDetails/CreditDetails'
					}) :''
				}else{
					uni.setStorageSync('Credit',this.CreditB)
					// index === 0 ? uni.navigateTo({
					// 	url:'/pages/debtStep/debtStep'
					// }) :''
					index === 0 ? uni.navigateTo({
						url:'/pages/PaymentRecords/PaymentRecords?id=2'
					}) :''
					index === 1 ? uni.navigateTo({
						url:'/pages/CreditDetails/CreditDetails'
					}) :''
				}
			},
			ClickBtn(){
				this.Eye = !this.Eye
			},
			GoNext(index){
					
				index === 0 ? uni.navigateTo({
					url:'/pages/FeelFreeLoan/FeelFreeLoan'
				}) :''
				index === 1 ? uni.navigateTo({
					url:'/pages/drawMoney/drawMoney'
				}) :''
			},
			ClickNext(index){
				console.log(index);
				index === 2 ? uni.navigateTo({
					url:'/pages/LimitInquiry/LimitInquiry'
				}) :''
				index === 4? uni.navigateTo({
					url:'/pages/FlowRrinting/FlowRrinting'
				}) :''
			},
			GO(index){
				// LoanRecords
				index === 4? uni.navigateTo({
					url:'/pages/LoanRecords/LoanRecords'
				}) :''
			}
		}
	}
</script>

<style lang="scss" scoped>
	.MyLoan{
		width: 100%;
		background-color: #f7f7f7;
		padding-bottom: 120rpx;
		.MyLoan-title{
			background-color: #fff;
			padding-bottom: 20rpx;
		}
		.MyLoan-Notlogin{
			width: 100%;
			height: 250rpx;
			background:url('@/static/MyLoan-image-1.png');
			background-size: 100% 100%;
			display: flex;
			align-items: center;
			justify-content: center;
			view{
				text-align: center;
				border: 1px solid;
				padding:10rpx 50rpx;
				border-radius: 50rpx;
			}
		}
		.MyLoan-login{
			width: 100%;
			height: 250rpx;
			background:url('@/static/MyLoan-image-1.png');
			background-size: 100% 100%;
			display: flex;
			justify-content: center;
			flex-wrap: wrap;
			align-items: center;
			view{
				width: 85%;
				display: flex;
				flex-wrap: wrap;
				align-items: center;
				line-height: 70rpx;
				.p{
					width: 100%;
					display: flex;
					align-items: center;
					font-size: 35rpx;
					image{
						width: 45rpx;
						height: 45rpx;
						margin-left: 20rpx;
					}
				}
				span{
					font-size: 50rpx;
					font-weight: bold;
				}
			}
		}
		.MyLoan-ListView{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			border-radius: 20rpx;
			background-color: #fff;
			padding: 20rpx 0;
			.ListView-title{
				width: 100%;
				padding: 20rpx;
				font-weight: bold;
				font-size: 35rpx;
				line-height: 60rpx;
				.SubTitle{
					font-size: 30rpx;
					color: #888;
				}
				.isTrue{
					font-size: 50rpx;
				}
			}
			.ListView-content{
				padding: 20rpx;
				display: flex;
				flex-wrap: wrap;
				line-height: 45rpx;
				font-size: 30rpx;
				span{
					width: 30%;
				}
				p{
					width:  70%;
					font-weight: bold;
				}
			}
			.ListView-btn{
				width: 100%;
				display: flex;
				margin-top: 20rpx;
				font-size: 30rpx;
				.btn{
					width: 50%;
					text-align: center;
					border-right: 1px solid #ccc;
				}
			}
		}
		.MyLoan-service{
			width: 90%;
			margin: 0 auto;
			
		}
		.loan-Setting{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
		}
	}
</style>