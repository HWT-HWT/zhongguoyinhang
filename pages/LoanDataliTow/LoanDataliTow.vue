<template>
	<view class="Loan-Datali">
		<view class="Loan-Datali-Tab">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' :RightMax='1' :isText='false' Color="#000">
				用款明细
			</backtaberVue>
		</view>
		<view class="Loan-Datali-Title" v-if="indexedDB == 1">
			<p>贷款金额(人民币元)</p>
			<span>900,000.00</span>
			<view class="Loan-Datali-ListView">
				<view class="ListView" v-for="(item,index) in LoanDataliList " :key="index" @click="Click(1)">
					<view class="name">
						{{item.name}}
					</view>
					<view class="text">
						{{item.text}}
					</view>
					<view class="menu" v-if="item.menu">
						{{item.menu}}
					</view>
				</view>
			</view>
		</view>
		<view class="Loan-Datali-View" v-if="indexedDB == 1">
			<view class="ListView" v-for="(item,index) in LoanDataliView " :key="index">
				<view class="name">
					{{item.name}} <br> <span v-if="index === 2">(单利)</span>
				</view>
				<view class="text" :style="{color:index === 9 ? '#1170f0' : '#000' }">
					{{item.text}}
				</view>
				<view class="menu" v-if="item.menu">
					{{item.menu}}
				</view>
			</view>
		</view>
		
		<view class="Loan-Datali-Title" v-if="indexedDB == 2">
			<p>贷款金额(人民币元)</p>
			<span>200.000.00</span>
			<view class="Loan-Datali-ListView">
				<view class="ListView" v-for="(item,index) in LoanDataliListTow " :key="index" @click="Click(2)">
					<view class="name">
						{{item.name}}
					</view>
					<view class="text">
						{{item.text}}
					</view>
					<view class="menu" v-if="item.menu">
						{{item.menu}}
					</view>
				</view>
			</view>
		</view>
		<view class="Loan-Datali-View" v-if="indexedDB == 2">
			<view class="ListView" v-for="(item,index) in LoanDataliViewTow " :key="index">
				<view class="name">
					{{item.name}} 
				</view>
				<view class="text" :style="{color:index === 10 ? '#1170f0' : '#000' }">
					{{item.text}}
				</view>
				<view class="menu" v-if="item.menu">
					{{item.menu}}
				</view>
			</view>
		</view>
		
		<view class="foot-View" @click="GoMoney">
			提前还款
		</view>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	import backtaberVue from '../../components/backtaber.vue'
	export default {
		data() {
			return {
				TitleImage:"../../static/back_black.png",
				rigthIcon:['../../static/boc_folder_title_service.png'],
				LoanDataliList:[
					{name:'本期还款日',text:'2025/06/01',menu:'还款记录'},
					{name:'本期截止当前应还利息',text:'672.73'},
					{name:'本期应还金额',text:'6,518.09'},
				],
				LoanDataliView:[
					{name:'贷款金额',text:'900,000.00'},
					{name:'年利率',text:'3.36%'},
					{name:'贷款期限',text:'36个月'},
					{name:'还款方式',text:'协议还款'},
					{name:'用款日',text:'2024/11/08'},
					{name:'贷款到期日',text:'2027/11/08'},
					{name:'还款账号',text:'6216 ****** 6429'},
					{name:'贷款机构名称',text:'中国银行广州大岭支行'},
					{name:'贷款机构地址',text:'广州市南沙区江南路110号首层、二层'},
					{name:'贷款机构电话',text:'02084987481'},
				],
				
				LoanDataliListTow:[
					{name:'本期还款日',text:'2025/06/11',menu:'还款记录'},
					{name:'截止当前应还利息',text:'188.88'},
					{name:'本期应还金额',text:'585.56'},
				],
				
				LoanDataliViewTow:[
					{name:'贷款金额',text:'200,000.00'},
					{name:'重定价日期',text:'2025/11/13'},
					{name:'还款方式',text:'按月还息 到期还本'},
					{name:'用款日',text:'2024/13/08'},
					{name:'贷款到期日',text:'2027/11/08'},
					{name:'还款账号',text:'6216 ****** 6429'},
					{name:'交易渠道',text:'手机银行提款'},
					{name:'资金用途',text:'日常消费'},
					{name:'贷款机构名称',text:'中国银行广州大岭支行'},
					{name:'贷款机构地址',text:'广州市南沙区江南路110号首层、二层'},
					{name:'贷款机构电话',text:'02084987481'},
				],
				footList:['用款记录','查看合同'],
				indexedDB:1
				
			}
		},
		components:{
			occupyVue,
			backtaberVue
		},
		methods: {
			GoNext(index){
				index === 0 ? uni.navigateTo({
					url:'/pages/PaymentRecords/PaymentRecords'
				}) : ''
				index === 1 ? uni.navigateTo({
					url:'/pages/contract/contract'
				}) : ''
			},
			Click(index){
				uni.navigateTo({
					url:`/pages/paymentHistory/paymentHistory?isTrue=${index}`
				})
			},
			GoMoney(){
				uni.navigateTo({
					url:`/pages/Repayment/Repayment`
				})
			}
		},
		onLoad(parma){
			console.log(parma.id);
			this.indexedDB = parma.id || 1
		}
	}
</script>

<style scoped lang="scss">
	.Loan-Datali{
		width: 100vw;
		height: 100vh;
		padding-bottom: 50rpx;
		background-color: #f4f4f4;
		.Loan-Datali-Tab{
			background-color: #fff;
		}
		.Loan-Datali-Title{
			background-color: #fff;
			padding: 40rpx;
			margin-bottom: 20rpx;
			p{
				font-weight: bold;
				font-size: 30rpx;
			}
			span{
				font-weight: bold;
				font-size: 50rpx;
			}
			.Loan-Datali-ListView{
				width: 100%;
				.ListView{
					display: flex;
					font-size: 28rpx;
					margin-top: 40rpx;
					.name{
						width: 30%;
						
					}
					.text{
						flex: 1;
						font-size: 28rpx;
						font-weight: bold;
					}
					.menu{
						
						width: 20%;
						color: #1170f0;
					}
				}
			}
		}
		.Loan-Datali-View{
			background-color: #fff;
			padding-bottom: 20rpx;
			.ListView{
				display: flex;
				font-size: 28rpx;
				padding:20rpx 40rpx;
				.name{
					width: 25%;
					color: #666;
				}
				.text{
					flex: 1;
					font-size: 28rpx;
					margin-left: 10rpx;
					font-weight: bold;
				}
				.menu{
					text-align: right;
					width: 20%;
					color: #1170f0;
				}
			}
		}
		.Loan-Datali-foot{
			width: 90%;
			margin: 0 auto;
			font-size: 25rpx;
			padding: 20rpx;
			span{
				color: #076aef;
			}
		}
		.Loan-Datali-foot-btn{
			display: flex;
			align-items: center;
			justify-content: center;
			margin-top: 20rpx;
			span{
				border-right:1px solid;
				padding:0 20rpx;
				font-size: 28rpx;
				color: #0066ef;
				font-weight: bold;
			}
		}
		.foot-View{
			width: 95%;
			margin: 0 auto;
			margin-top: 50rpx;
			padding: 20rpx 0;
			display: flex;
			justify-content: center;
			border: 1px solid ;
			font-weight: bold;
			color:#076aef;
			font-size: 30rpx;
		}
	}
</style>
