<template>
	<view class="live">
		<view class="live-title">
			<occupyVue :hight="'90rpx'"></occupyVue>
			<HeadTitleVue :menu='TitleMenu'  :IconSize="HeaderIconSize"  Icon="../../static/icon_new_life_white_location.png" :isTrue="false">
				--
			</HeadTitleVue>
		</view>
		<view class="live-Scroll-Title" v-if="!ScrollTop == 0" :style="{opacity:`${ScrollTop / 100 }`}">
			<occupyVue :hight="'90rpx'"></occupyVue>
			<HeadTitleVue :menu='TitleMenuBlack' TextColor="#000" :IconSize="HeaderIconSize"  Icon="../../static/icon_new_life_location.png" :isTrue="false" >
				--
			</HeadTitleVue>
		</view>
		<view class="live-Swiper">
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item>
					<image src="@/static/live-bg-1.png" mode=""></image>
				</swiper-item>
				<swiper-item>
					<image src="@/static/live-bg-2.png" mode=""></image>
				</swiper-item>
			</swiper>
		</view>
		<view class="live-View">
			<ListViewVue :listTitle="ListViewList" FontSize="25rpx" Pad="30rpx 10rpx"></ListViewVue>
		</view>
		<view class="live-ListView">
			<ListViewVue :listTitle='ViewList' width="20%" :Pad="'40rpx 0'" FontSize="25rpx"></ListViewVue>
		</view>
		<view class="live-PreferredView">
			<titleVue LFontSize="38">
				<template #left>
					为您优选
				</template>
			</titleVue>
			<view class="live-Preferred">
				<view class="PreferredView" v-for="(item,index) in PreferredList" :key="index">
					<image :src="item.image" mode=""></image>
					<p>{{item.Title}}</p>
					<span>{{item.SubTitle}}</span>
				</view>
			</view>
		</view>
		<view class="live-DepositView">
			<titleVue LFontSize="38">
				<template #left>
					话费充值
				</template>
			</titleVue>
			<view class="live-Deposit">
				<view class="Deposit">
					<view class="Deposit-Input">
						<span>号码</span>
						<input type="text" placeholder="请输入充值号码" />
						<image src="@/static/Deposit-icon-1.png" mode=""></image>
					</view>
					<view class="Deposit-btn">
						<view class="btn">
							50
						</view>
						<view class="btn">
							100
						</view>
						<view class="btn">
							200
						</view>
					</view>
					<p>本服务不提供运营商发票 详情查看 <span>全部说明</span></p>
				</view>
			</view>
		</view>
		<view class="Live-tabs">
			 <z-tabs ref="tabs" :list="tabList" :current="current" active-color='#e2003b' scroll-count='4' tab-width='150rpx' bar-width="150rpx" :active-style='{color:"#000",transform: "scale(1.2)"}'/>
			<view class="scroll-view">
				<view class="Optimal-title-btn">
					<view class="Optimal-btn" v-for="(item,index) in wealthInvest" :key="index">
						{{item}}
					</view>
				</view>
			</view>
			<view v-for="(sum,num) in tabsLise" :key="num">
				<titleVue LFontSize="38">
					<template #left>
						{{sum.name}}
					</template>
				</titleVue>
				<view class="live-Preferred">
					<view class="PreferredView" v-for="(item,index) in sum.PreferredList" :key="index">
						<image :src="item.image" mode=""></image>
						<p>{{item.Title}}</p>
						<span>{{item.SubTitle}}</span>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	import HeadTitleVue from '../../components/HeadTitle.vue'
	import SeachTitle from '../../components/SeachTitle.vue'
	import ListViewVue from '../../components/ListView.vue'
	import titleVue from '../../components/titleVue.vue'
	import scrollBtnVue from '../../components/scroll-btn.vue'
	export default {
		data() {
			return {
				TitleMenu:[
					{name:'扫一扫',image:'../../static/boc_folder_title_white_scan.png'},
					{name:'客服',image:'../../static/boc_folder_title_white_service.png'}
				],
				TitleMenuBlack:[
					{name:'扫一扫',image:'../../static/boc_folder_title_scan.png'},
					{name:'客服',image:'../../static/boc_folder_title_service.png'}
				],
				ScrollTop:0,
				HeaderIconSize:['35rpx','40rpx'],
				ListViewList:[
					{name:'生活缴费',icon:'../../static/live-icon-1.png'},
					{name:'话费充值',icon:'../../static/live-icon-2.png'},
					{name:'城市服务',icon:'../../static/live-icon-3.png'},
					{name:'福仔云游记',icon:'../../static/live-icon-4.png'}
				],
				ViewList:[
					{name:'政务服务',icon:'../../static/liveView-icon-1.png'},
					{name:'纪念币预约',icon:'../../static/liveView-icon-2.png'},
					{name:'全国住房公积金',icon:'../../static/liveView-icon-3.png'},
					{name:'网点排队',icon:'../../static/liveView-icon-4.png'},
					{name:'实物贵金属',icon:'../../static/liveView-icon-5.png'},
					{name:'外卖',icon:'../../static/liveView-icon-6.png'},
					{name:'立减金月月领',icon:'../../static/liveView-icon-7.png'},
					{name:'尊享权益',icon:'../../static/liveView-icon-8.png'},
					{name:'智慧食堂',icon:'../../static/liveView-icon-9.png'},
					{name:'更多',icon:'../../static/liveView-icon-10.png'},
				],
				PreferredList:[
					{image:'../../static/Preferred-icon-1.png',Title:'签到挑战',SubTitle:'领立减金'},
					{image:'../../static/Preferred-icon-2.png',Title:'代发客户...',SubTitle:'代发客户专区'},
					{image:'../../static/Preferred-icon-3.png',Title:'信用卡客...',SubTitle:'缤纷生活'},
					{image:'../../static/Preferred-icon-4.png',Title:'社保卡专区',SubTitle:'一卡通用'},
					{image:'../../static/Preferred-icon-5.png',Title:'美团数币...',SubTitle:'点亮数币美...'},
					{image:'../../static/Preferred-icon-6.png',Title:'福蛇迎春...',SubTitle:'北京地区新...'}
				],
				tabList: ['精选','本地专属','公益驿站','实物贵金属','特殊资产'],
				current: 0,
				wealthInvest:['中行推荐','乐享购物','特色专区','美食生鲜'],
				tabsLise:[
					{
						name:'中行推荐',
						PreferredList:[
							{image:'../../static/Preferred-icon-1.png',Title:'签到挑战',SubTitle:'领立减金'},
							{image:'../../static/Preferred-icon-2.png',Title:'代发客户...',SubTitle:'代发客户专区'},
							{image:'../../static/Preferred-icon-3.png',Title:'信用卡客...',SubTitle:'缤纷生活'},
							{image:'../../static/Preferred-icon-4.png',Title:'社保卡专区',SubTitle:'一卡通用'},
							{image:'../../static/Preferred-icon-5.png',Title:'美团数币...',SubTitle:'点亮数币美...'},
							{image:'../../static/Preferred-icon-6.png',Title:'福蛇迎春...',SubTitle:'北京地区新...'}
						],
					},
					{
						name:'乐享购物',
						PreferredList:[
							{image:'../../static/Preferred-icon-1.png',Title:'签到挑战',SubTitle:'领立减金'},
							{image:'../../static/Preferred-icon-2.png',Title:'代发客户...',SubTitle:'代发客户专区'},
							{image:'../../static/Preferred-icon-3.png',Title:'信用卡客...',SubTitle:'缤纷生活'},
							{image:'../../static/Preferred-icon-4.png',Title:'社保卡专区',SubTitle:'一卡通用'},
							{image:'../../static/Preferred-icon-5.png',Title:'美团数币...',SubTitle:'点亮数币美...'},
							{image:'../../static/Preferred-icon-6.png',Title:'福蛇迎春...',SubTitle:'北京地区新...'}
						],
					},
					{
						name:'特色专区',
						PreferredList:[
							{image:'../../static/Preferred-icon-1.png',Title:'签到挑战',SubTitle:'领立减金'},
							{image:'../../static/Preferred-icon-2.png',Title:'代发客户...',SubTitle:'代发客户专区'},
							{image:'../../static/Preferred-icon-3.png',Title:'信用卡客...',SubTitle:'缤纷生活'},
							{image:'../../static/Preferred-icon-4.png',Title:'社保卡专区',SubTitle:'一卡通用'},
							{image:'../../static/Preferred-icon-5.png',Title:'美团数币...',SubTitle:'点亮数币美...'},
							{image:'../../static/Preferred-icon-6.png',Title:'福蛇迎春...',SubTitle:'北京地区新...'}
						],
					},
					{
						name:'美食生鲜',
						PreferredList:[
							{image:'../../static/Preferred-icon-1.png',Title:'签到挑战',SubTitle:'领立减金'},
							{image:'../../static/Preferred-icon-2.png',Title:'代发客户...',SubTitle:'代发客户专区'},
							{image:'../../static/Preferred-icon-3.png',Title:'信用卡客...',SubTitle:'缤纷生活'},
							{image:'../../static/Preferred-icon-4.png',Title:'社保卡专区',SubTitle:'一卡通用'},
							{image:'../../static/Preferred-icon-5.png',Title:'美团数币...',SubTitle:'点亮数币美...'},
							{image:'../../static/Preferred-icon-6.png',Title:'福蛇迎春...',SubTitle:'北京地区新...'}
						],
					}
				]
			}
		},
		methods: {
			
		},
		components:{
			occupyVue,
			HeadTitleVue,
			SeachTitle,
			ListViewVue,
			titleVue,
			scrollBtnVue
		},
		onPageScroll(Scroll) {
			this.ScrollTop = Scroll.scrollTop
		}
	}
</script>

<style scoped lang="scss">
	.live{
		width: 100vw;
		padding-bottom: 50rpx;
		.live-title{
			position: absolute;
			top: 0;
			z-index: 999;
		}
		.live-Scroll-Title{
			background-color: #fff;
			position: fixed;
			top: 0;
			z-index: 998;
			padding-bottom: 20rpx;
		}
		.live-Swiper{
			width: 100%;
			height: 450rpx;
			position: relative;
			top: 0;
			swiper{
				width: 100%;
				height: 100%;
				/deep/.uni-swiper-dot{
					width: 10rpx;
					height: 5rpx;
					border-radius: 10rpx;
					background-color: #f7f7f7;
					display: none;
				}
				/deep/.uni-swiper-dot-active{
					width: 20rpx;
					height: 5rpx;
					border-radius: 10rpx;
					background-color: #fff;
					display: none;
				}
				swiper-item{
					width: 100%;
					height: 100%;
					image{
						width: 100%;
						height: 100%;
					}
				}
			}
		}
		.live-View{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			background-color: #fff;
			border-radius: 10rpx;
			box-shadow: 00 1rpx 10rpx rgba(0, 0, 0, .1);
			margin-top: -50rpx;
			z-index: 900;
			position: relative;
		}
		.live-PreferredView{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			.live-Preferred{
				width: 100%;
				display: flex;
				flex-wrap: wrap;
				justify-content: space-evenly;
				align-items: center;
				background: linear-gradient(to bottom, #fddac3 60%, #fffefc);
				border-radius: 20rpx;
				border:1px solid #ddd;
				padding-bottom: 20rpx;
				.PreferredView{
					text-align: center;
					margin-top: 30rpx;
					
					image{
						width:180rpx;
						height:190rpx;
					}
					p{
						font-size: 34rpx;
						font-weight: bold;
					}
					span{
						color:#555;
						font-size: 28rpx;
					}
				}
			}
		}
		.live-DepositView{
			width: 90%;
			margin: 0 auto;
			.live-Deposit{
				margin: 0 auto;
				background: #f9f9f9;
				margin-top: 20rpx;
				padding: 20rpx;
				border-radius:20rpx;
				.Deposit{
					background-color: #fff;
					padding: 20rpx;
					.Deposit-Input{
						display: flex;
						align-items: center;
						justify-content: space-evenly;
						border-bottom: 1rpx solid #ccc;
						padding-bottom: 20rpx;
						align-items: center;
						span{
							font-size: 35rpx;
							font-weight: bold;
						}
						input{
							font-size: 35rpx;
						}
						image{
							width: 70rpx;
							height: 70rpx;
						}
					}
					.Deposit-btn{
						display: flex;
						justify-content: space-between;
						margin-top: 10rpx;
						.btn{
							margin-top: 20rpx;
							padding: 20rpx 50rpx;
							border-radius: 20rpx;
							border: 1px solid #000 ;
							font-size: 40rpx;
							font-weight: bold;
							color: #555;
						}
					}
					p{
						padding: 20rpx;
						font-size: 28rpx;
						span{
							color: #1c67b8;
							margin-left: 5rpx;
						}
					}
				}
			}
		}
		.Live-tabs{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			.scroll-view{
				width: 100%;
				margin: 30rpx auto;
				display: flex;
				justify-content: space-between;
				.Optimal-title-btn{
					width: 100%;
					padding-left: 10rpx;
					display: flex;
					align-items: center;
					.Optimal-btn{
						margin-right: 30rpx;
						height: 45rpx;
						padding: 5rpx 20rpx;
						border-radius: 40rpx;
						font-size: 25rpx;
						background-color: #fef5f6;
						color: #333;
						display: flex; 	
						align-items: center;
					}
					.Optimal-btn:hover{
						color:#fff;
						background-color: #cb0c35;
					}
				}
			}
			.live-Preferred{
				width: 100%;
				display: flex;
				flex-wrap: wrap;
				justify-content: space-between;
				align-items: center;
				border-radius: 20rpx;
				padding-bottom: 20rpx;
				.PreferredView{
					margin-top: 30rpx;
					box-shadow: 0 0 10rpx 1rpx rgba(0, 0, 0, .2);
					border-radius:10rpx;
					padding-bottom: 20rpx;
					image{
						width:330rpx;
						height:330rpx;
					}
					p{
						font-size: 32rpx;
						font-weight: bold;
						padding:20rpx;
					}
					span{
						color:#555;
						font-size: 28rpx;
						padding:0 20rpx;
					}
				}
			}
		}
	}
</style>
