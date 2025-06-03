<template>
	<view class="Wealth">
		<view class="Wealth-Title">
			<occupyVue hight="90rpx"></occupyVue>
			<HeadTitleVue :menu='TitleMenu' TextColor="#000">
				登录
			</HeadTitleVue>
		</view>
		<view class="Wealth-Fixed"  v-if="!ScrollTop == 0" :style="{opacity:`${ScrollTop / 100 }`}">
			<occupyVue hight="90rpx"></occupyVue>
			<HeadTitleVue :menu='TitleMenu' TextColor="#000">
				登录
			</HeadTitleVue>
		</view>
		<view class="Wealth-Balance">
			<p>总资产(折算人民币元)</p>
			<span v-if='!token'>登录查看 <image src="../../static/boc_arrow_right_white.png" mode=""></image> </span>
			<span v-else>45,084.39 <image src="../../static/boc_arrow_right_white.png" mode=""></image> </span>
		</view>
		<view class="Wealth-List">
			<ListViewVue :listTitle='ViewList' :Pad="'30rpx 0'" FontSize="25rpx"></ListViewVue>
		</view>
		<view class="Wealth-Row">
			<view class="Row">
				上证50 
				<span>
					2654.98 
					<image src="../../static/boc_home_rate_arrow_up.png" mode=""></image>
				</span>
			</view>
			<view class="Row" style="color: #9b2a44;">
				11.75
				<span>
					0.44% 
					<image style="width: 13rpx; height: 22rpx;" src="../../static/icon_account_right_arrows.png" mode=""></image>
				</span>
			</view>
		</view>
		<view class="Wealth-Swiper">
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item v-for="(item,index) in 3" :key="index">
					<image :src="`../../static/Wealth-Swiper-${index+1}.png`" mode=""></image>
				</swiper-item>
			</swiper>
		</view>
		<view class="Wealth-Manage">
			<titleVue LFontSize="38" :icon="true" IconSize="1.5">
				<template #left>
					按期理财
				</template>
			</titleVue>
			<scrollBtnVue :list="wealthInvest"></scrollBtnVue>
			<p>近几天要用的钱就选日日盈</p>
			<view class="ListView">
				<view class="ListView-Box" v-for="(item,index) in ManageList" :key="index">
					<view class="Name">
						<p>{{item.LeftName}}</p>
						<span>{{item.LeftSubName}}</span>
					</view>
					<view class="SubName">
						<p>{{item.RightName}}</p>
						<span>{{item.RightSubName}}</span>
					</view>
				</view>
				<view class="Refresh">
					<image src="../../static/boc_reload.png" mode=""></image> 换一换
				</view>
			</view>
			<image class="Manage-image" src="@/static/Manage-bg-1.png" mode=""></image>
		</view>
		<view class="Wealth-Theme">
			<titleVue LFontSize="38" :icon="true" IconSize="1.5">
				<template #left>
					热门主题
				</template>
			</titleVue>
			<scrollBtnVue :list="ThemeList"></scrollBtnVue>
			<p>指数成长,分享未来</p>
			<view class="ListView">
				<view class="ListView-Box" v-for="(item,index) in ThemeListView" :key="index">
					<view class="Name">
						<p>{{item.LeftName}}</p>
						<span>{{item.LeftSubName}}</span>
					</view>
					<view class="SubName">
						<p>{{item.RightName}}</p>
						<span>{{item.RightSubName}}</span>
					</view>
				</view>
				<view class="Refresh">
					<image src="../../static/boc_reload.png" mode=""></image> 换一换
				</view>
			</view>
		</view>
		<view class="Wealth-Four">
			<titleVue LFontSize="38" :icon="true" IconSize="1.5">
				<template #left>
					轻松配置“四笔钱”
				</template>
			</titleVue>
			<scrollBtnVue :list="FourList"></scrollBtnVue>
			<p>流动性强，兼顾收益与灵活性</p>
			<view class="ListView">
				<view class="ListView-Box" v-for="(item,index) in FourListView" :key="index">
					<view class="Name">
						<p>{{item.LeftName}}</p>
						<span>{{item.LeftSubName}}</span>
					</view>
					<view class="SubName">
						<p>{{item.RightName}}</p>
						<span>{{item.RightSubName}}</span>
					</view>
				</view>
				<view class="Refresh">
					<image src="../../static/boc_reload.png" mode=""></image> 换一换
				</view>
			</view>
		</view>
		<view class="Wealth-Point">
			<titleVue LFontSize="38" :icon="true" IconSize="1.5">
				<template #left>
					机构观点
				</template>
			</titleVue>
			<view class="Point-ListView">
				<view class="Title">
					<image src="@/static/Point-logo-1.png" mode=""></image>
					<view class="TitleCentent">
						前海开源基金
						<view class="View">
						千亿级投资资产管理机构,11年7座金牛奖
						</view>
					</view>
					<image class="icon" src="@/static/arrow_white.png" mode=""></image>
					<p class="p"><span>02-26</span> 投研观点重磅会议临近，有何期...</p>
				</view>
				<view class="Colman">
					<view class="Title">
						<image src="@/static/Point-logo-2.png" mode=""></image>
						<view class="TitleCentent">
							易方达..
						</view>
						<image class="icon" src="@/static/arrow_white.png" mode=""></image>
						<p class="p">为什么投资科创综指?(5)</p>
						
						<view class="Eye">
							
							<view><image src="@/static/icon_folder_eye_open.png" mode=""></image> 4</view>
							
							<span>02-26</span>
							
						</view>
					</view>
					<view class="Title">
						<image src="@/static/Point-logo-3.png" mode=""></image>
						<view class="TitleCentent">
							平安理财
						</view>
						<image class="icon" src="@/static/arrow_white.png" mode=""></image>
						<p class="p">市场观察站|一图速览本周市场研...</p>
						
						<view class="Eye">
							
							<view><image src="@/static/icon_folder_eye_open.png" mode=""></image> 100</view>
							
							<span>02-26</span>
							
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="Wealth-Info">
			<titleVue LFontSize="38" :icon="true" IconSize="1.5">
				<template #left>
					资讯
				</template>
			</titleVue>
			<view class="Info-MaxView">
				<image src="../../static/Info-bg-1.png" mode=""></image>
				<view class="ListView">
					<p>【A股港股携手上涨】中银资产配置日报2...</p>
					<view class="SubText">
						<span>中国银行投资策略...</span>
						<view class="p">02-27 <image src="../../static/icon_folder_eye_open.png" mode=""></image> 477</view>
						<view class="p"> <image src="@/static/Info-Zan-1.png" mode=""></image> 4 </view>
					</view>
				</view>
			</view>
		</view>
		<view class="Wealth-Info-ListView" v-for="(item,index) in InfoList" :key="index">
			<view class="NameImage">
				<p>{{item.title}}</p>
				<image :src="item.image" mode=""></image>
			</view>
			<view class="SubText">
				<span>{{item.SubTitle}}</span>
				<view class="p"><image src="../../static/icon_folder_eye_open.png" mode=""></image>  {{item.Look}}</view>
				<view class="p"> <image src="@/static/Info-Zan-1.png" mode=""></image> {{item.Z}} </view>
			</view>
		</view>
	</view>
</template>

<script>
	import HeadTitleVue from '../../components/HeadTitle.vue';
	import occupyVue from '../../components/occupy.vue';
	import ListViewVue from '../../components/ListView.vue';
	import titleVue from '../../components/titleVue.vue';
	import scrollBtnVue from '../../components/scroll-btn.vue'
	export default {
		data() {
			return {
				TitleMenu:[
					{name:'购物车',image:'../../static/Shopping_Car.png'},
					{name:'客服',image:'../../static/boc_folder_title_service.png'}
				],
				ScrollTop:0,
				ViewList:[
					{name:'理财',icon:'../../static/Wealth-icon-1.png'},
					{name:'存款管理',icon:'../../static/Wealth-icon-2.png'},
					{name:'结汇购汇',icon:'../../static/Wealth-icon-3.png'},
					{name:'基金',icon:'../../static/Wealth-icon-4.png'},
					{name:'结构性存款',icon:'../../static/Wealth-icon-5.png'},
					{name:'活钱宝',icon:'../../static/Wealth-icon-6.png'},
					{name:'账户贵金属',icon:'../../static/Wealth-icon-7.png'},
					{name:'贵金属积存',icon:'../../static/Wealth-icon-8.png'},
					{name:'中银慧投',icon:'../../static/Wealth-icon-9.png'},
					{name:'更多',icon:'../../static/Wealth-icon-10.png'},
				],
				wealthInvest:['日日盈','月月盈','季季盈','年年盈'],
				ThemeList:['指数投资','红利投资','美元投资'],
				FourList:['灵活','稳健','进取','保障'],
				ManageList:[
					{LeftName:'3.71%',LeftSubName:'成立以来年化',RightName:'中银理财-稳富信用…',RightSubName:'精挑细选 灵活申赎'},
					{LeftName:'3.99%',LeftSubName:'成立以来年化',RightName:'信银理财安盈象固收…',RightSubName:'活钱理财 运作稳健'},
					{LeftName:'3.71%',LeftSubName:'成立以来年化',RightName:'交银理财稳享灵动慧…',RightSubName:'申赎灵活 策略稳健'}
				],
				ThemeListView:[
					{LeftName:'19.84%',LeftSubName:'成立以来涨幅',RightName:'中银MSCI中国A50…',RightSubName:'R4中高风险'},
					{LeftName:'20.32%',LeftSubName:'近6月涨幅',RightName:'平安中证A50交易型…',RightSubName:'R4中高风险'},
					{LeftName:'30.51%',LeftSubName:'成立以来涨幅',RightName:'宏利沪深300指数增…',RightSubName:'R3中等风险'}
				],
				FourListView:[
					{LeftName:'活钱宝',LeftSubName:'R1风险',RightName:'丰富多样增值服务',RightSubName:'1分起购'},
					{LeftName:'4.45%',LeftSubName:'成立以来年化',RightName:'申赎灵活 稳健策略',RightSubName:'中银理财-稳富信用精选稳'},
					{LeftName:'3.99%',LeftSubName:'成立以来年化',RightName:'每日开放 运作稳健',RightSubName:'信银理财安盈象固收稳利日'}
				],
				InfoList:[
					{title:'A股上涨，沪深300涨近1%|指数日报',SubTitle:'东方基金财富号 02-26',image:'../../static/info-bg-2.png',Z:0,Look:'144'},
					{title:'债市继续反弹|2.26债市情报局',SubTitle:'东方基金财富号 02-26',image:'../../static/info-bg-3.png',Z:8,Look:'414'},
					{title:'CIO观点|新政府的不确定性带来反垄断售虑',SubTitle:'NB路博迈基金 02-26',image:'../../static/info-bg-4.png',Z:0,Look:'89'}
				],
				token:''
			};
		},
		components:{
			HeadTitleVue,
			occupyVue,
			ListViewVue,
			titleVue,
			scrollBtnVue
		},
		onPageScroll(Scroll) {
			this.ScrollTop = Scroll.scrollTop
		},
		created() {
			this.token = uni.getStorageSync('account')
		}
	}
</script>

<style lang="scss" scoped>
	.Wealth{
		width: 100vw;
		padding-bottom: 50rpx;
		.Wealth-Fixed{
			width: 100%;
			position: fixed;
			background-color: #fff;
			z-index: 999;
			top: 0;
			padding-bottom: 20rpx;
		}
		.Wealth-Balance{
			width: 90%;
			height: 200rpx;
			margin: 0 auto;
			margin-top: 20rpx;
			background: url('@/static/Wealth-bg-1.png');
			background-size: 100% 100%;
			p{
				color: #fff;
				padding: 30rpx;
				font-size: 28rpx;
			}
			span{
				color: #fff;
				font-size: 40rpx;
				font-weight: bold;
				padding: 30rpx;
				image{
					width: 15rpx;
					height: 25rpx;
					margin-left:20rpx;
				}
			}
		}
		.Wealth-ListView{
			width: 90%;
			margin: 0 auto;
			margin-top: 30rpx;
			border-radius: 20rpx;
			box-shadow: 0 0 10rpx 1rpx rgba(0, 0, 0, .1);
			display: flex;
			flex-wrap: wrap;
			justify-items: center;
			p{
				width: 100%;
				font-size: 34rpx;
				font-weight: bold;
				text-align: center;
				margin-top: 40rpx;
			}
			.Login{
				padding:15rpx 50rpx;
				font-weight: bold;
				border-radius: 50rpx;
				background-color: #df2d47;
				color: #fff;
				margin: 50rpx auto;
			}
			.FooterText{
				width: 100%;
				padding: 20rpx;
				background:linear-gradient(to right ,#f4e9d7,#e1cead);
				font-size: 28rpx;
				color: #563209;
				border-radius: 0 0 20rpx 20rpx;
			}
		}
		.Wealth-Row{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			display: flex;
			justify-content: space-between;
			align-items: center;
			font-size: 28rpx;
			.Row{
				span{
					margin-left: 20rpx;
					color: #b01a47;
					image{
						width: 20rpx;
						height: 25rpx;
						margin-left: 15rpx;
					}
				}
			}
		}
		.Wealth-Swiper{
			width: 90%;
			margin: 0 auto;
			height: 450rpx;
			margin-top: 20rpx;
			swiper{
				width: 100%;
				height: 100%;
				::v-deep .uni-swiper-dots-horizontal{
					bottom: 15rpx;
				}
				::v-deep.uni-swiper-dot{
					width: 10rpx;
					height: 5rpx;
					border-radius: 10rpx;
				}
				::v-deep.uni-swiper-dot-active{
					width: 20rpx;
					height: 5rpx;
					border-radius: 10rpx;
					background-color: #bf1438;
				}
				swiper-item{
					image{
						width: 100%;
						height: 100%;
					}
				}
			}
		}
		.Wealth-Manage{
			width: 90%;
			margin: 0 auto;
			p{
				color: #ac805f;
				font-size: 28rpx;
				margin-top: 10rpx;
			}
			.ListView{
				width: 100%;
				background-color: #fcfbf7;
				margin-top: 20rpx;
				border-radius: 20rpx;
				padding-bottom: 20rpx;
				.ListView-Box{	
					display: flex;
					justify-content: space-between;
					padding: 30rpx;
					line-height: 60rpx;
					.Name{
						p{
							font-weight: bold;
							font-size: 40rpx;
						}
						span{
							font-size: 28rpx;
							color: #696864;
						}
					}
					.SubName{
						width: 60%;
						p{
							width: 100%;
							font-weight: bold;
							color: #000;
							font-size: 35rpx;
						}
						span{
							font-size: 28rpx;
							border: 1px solid #8c8b87;
							padding:5rpx 10rpx;
							color: #6a6965;
						}
					}
				}
				.Refresh{
					width: 100%;
					display: flex;
					align-items: center;
					color: #686763;
					justify-content: center;
					font-size: 30rpx;
					margin-top: 10rpx;
					image{
						width: 50rpx;
						height: 50rpx;
						margin-right: 20rpx;
					}
				}
			}
			.Manage-image{
				width: 100%;
				height: 180rpx;
				margin-top: 40rpx;
			}
		}
		.Wealth-Theme{
			width: 90%;
			margin: 0 auto;
			p{
				color: #ac805f;
				font-size: 28rpx;
				margin-top: 10rpx;
			}
			.ListView{
				width: 100%;
				background-color: #fcfbf7;
				margin-top: 20rpx;
				border-radius: 20rpx;
				padding-bottom: 20rpx;
				.ListView-Box{	
					display: flex;
					justify-content: space-between;
					padding: 30rpx;
					line-height: 60rpx;
					.Name{
						p{
							font-weight: bold;
							font-size: 40rpx;
						}
						span{
							font-size: 28rpx;
							color: #696864;
						}
					}
					.SubName{
						width: 60%;
						p{
							width: 100%;
							font-weight: bold;
							color: #000;
							font-size: 35rpx;
						}
						span{
							font-size: 28rpx;
							border: 1px solid #8c8b87;
							padding:5rpx 10rpx;
							color: #6a6965;
						}
					}
				}
				.Refresh{
					width: 100%;
					display: flex;
					align-items: center;
					color: #686763;
					justify-content: center;
					font-size: 30rpx;
					margin-top: 10rpx;
					image{
						width: 50rpx;
						height: 50rpx;
						margin-right: 20rpx;
					}
				}
			}
		}
		.Wealth-Four{
			width: 90%;
			margin: 0 auto;
			p{
				color: #ac805f;
				font-size: 28rpx;
				margin-top: 10rpx;
			}
			.ListView{
				width: 100%;
				background-color: #fcfbf7;
				margin-top: 20rpx;
				border-radius: 20rpx;
				padding-bottom: 20rpx;
				.ListView-Box{	
					display: flex;
					justify-content: space-between;
					padding: 30rpx;
					line-height: 60rpx;
					.Name{
						p{
							font-weight: bold;
							font-size: 40rpx;
						}
						span{
							font-size: 28rpx;
							color: #696864;
						}
					}
					.SubName{
						width: 60%;
						p{
							width: 100%;
							font-weight: bold;
							color: #000;
							font-size: 35rpx;
						}
						span{
							font-size: 28rpx;
							border: 1px solid #8c8b87;
							padding:5rpx 10rpx;
							color: #6a6965;
						}
					}
				}
				.Refresh{
					width: 100%;
					display: flex;
					align-items: center;
					color: #686763;
					justify-content: center;
					font-size: 30rpx;
					margin-top: 10rpx;
					image{
						width: 50rpx;
						height: 50rpx;
						margin-right: 20rpx;
					}
				}
			}
		}
		.Wealth-Point{
			width: 90%;
			margin: 0 auto;
			.Point-ListView{
				width: 100%;
				margin: 0 auto;
				border-radius: 20rpx;
				.Title{
					background-color: #f1f5fe;
					display: flex;
					padding: 30rpx;
					justify-content: space-between;
					align-items: center;
					flex-wrap: wrap;
					border-radius: 20rpx;
					image{
						width: 50rpx;
						height: 50rpx;
					}
					.TitleCentent{
						font-size: 30rpx;
						font-size: 35rpx;
						font-weight: bold;
						.View{
							font-size: 25rpx;
							font-weight: normal;
							border: 1px solid;
							margin:20rpx 0;
						}
					}
					p{
						width: 100%;
						font-size: 34rpx;
						span{
							font-size: 30rpx;
							margin-right:20rpx ;
						}
					}
				}
				.Colman{
					width: 100%;
					display: flex;
					justify-content: space-between;
					margin-top: 20rpx;
					.Title{
						width: 40%;
						display: flex;
						justify-content: space-between;
						align-items: center;
						flex-wrap: wrap;
						image{
							width: 50rpx;
							height: 50rpx;
						}
						.TitleCentent{
							font-size: 35rpx;
							font-weight: bold;
							.View{
								font-size: 25rpx;
								font-weight: normal;
								border: 1px solid;
								margin:20rpx 0;
							}
						}
						.p{
							width: 100%;
							font-size: 30rpx;
							margin-top: 20rpx;
						}
						.Eye{
							width: 100%;
							display: flex;
							justify-content: space-between;
							align-items: center;
							margin-top: 20rpx;
							font-size: 28rpx;
							view{
								display: flex;
								align-items: center;
								image{
									width: 40rpx;
									height: 30rpx;
									margin-right: 10rpx;
								}
							}
							span{
								display: flex;
								justify-content: space-between;
								align-items: center;
							}
							
						}
					}
				}
			}
		}
		.Wealth-Info{
			width: 90%;
			margin: 0 auto;
			.Info-MaxView{
				display: flex;
				flex-wrap: wrap;
				image{
					width: 100%;
					height: 450rpx;
				}
				.ListView{
					width: 100%;
					p{
						width: 100%;
						margin-top: 20rpx;
					}
					.SubText{
						display: flex;
						justify-content: space-between;
						align-items: center;
						padding: 20rpx;
						span{
							font-size: 28rpx;
						}
						.p{
							display: flex;
							justify-content: space-between;
							align-items: center;
							font-size: 28rpx;
							image{
								width: 38rpx;
								height: 32rpx;
								margin:0 10rpx;
							}
						}
					}
				}
			}
		}
		.Wealth-Info-ListView{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			border-bottom:1px solid #ddd;
			.NameImage{
				display: flex;
				justify-content: space-between;
				padding: 10rpx;
				p{
					margin-top: 20rpx;
					font-size: 30rpx;
					font-weight: bold;
				}
				image{
					width: 300rpx;
					height: 160rpx;
				}
			}
			.SubText{
						display: flex;
						justify-content: space-between;
						align-items: center;
						padding: 20rpx;
						span{
							font-size: 28rpx;
						}
						.p{
							display: flex;
							justify-content: space-between;
							align-items: center;
							font-size: 28rpx;
							image{
								width: 38rpx;
								height: 32rpx;
								margin:0 10rpx;
							}
						}
					}
		}
	}
</style>
