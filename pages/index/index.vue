<template>
	<view class="index">
		<view class="index-title"  v-show="true">
			<occupyVuew :hight="'90rpx'"></occupyVuew>
			<HeadTitleVue :menu='TitleMenu' :Icon='Icon' v-if="!token" >
				登录
			</HeadTitleVue>
			<HeadTitleVue :menu='TitleMenu' :Icon='"../../static/boc_en_logout.png"' v-else :isTrue="false" >
				退出
			</HeadTitleVue>
		</view>
		<view class="index-Scroll-Title" v-if="!ScrollTop == 0" :style="{opacity:`${ScrollTop / 100 }`}">
			<occupyVuew :hight="'90rpx'"></occupyVuew>
			<HeadTitleVue :menu='TitleMenuBlack' :Icon='Iconblack' v-if="!token" TextColor="#000">
				登录
			</HeadTitleVue>
			<HeadTitleVue :menu='TitleMenuBlack' :Icon='"../../static/boc_en_logout_gray.png"' v-else :isTrue="false" TextColor="#000" >
				退出
			</HeadTitleVue>
		</view>
		<view class="index-IconView">
			<view class="IconView" v-for="(item,index) in IconView" :key="index" @click="IconViewIndex(index)">
				<image :src="`../../static/index-NavTitle-Icon-${index+1}.png`" mode=""></image>
				<span>{{item}}</span>
			</view>
		</view>
		<view class="index-ListView">
			<ListView :listTitle='ViewList' :Pad="'30rpx 0'" FontSize="25rpx" @ClickNext='Next'></ListView>
		</view>
		<view class="index-Notice">
			<view class="Notice-Text">
				<image src="@/static/notice-bg-1.png" mode=""></image>
				<view class="">
					<p>【2024年平均工资出炉】中银资</p>
					<p>产配置日报20250519</p>
				</view>
			</view>
			<image class="IconRight" src="@/static/arrow_white.png" mode=""></image>
		</view>
		<view class="index-banner">
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item v-for="(item,index) in 4" :key="index">
					<image :src="`../../static/index-banner-${index+1}.png`" mode=""></image>
				</swiper-item>
			</swiper>
		</view>
		<view class="index-recommend">
			<titleVue LFontSize="38">
				<template #left>
					为您推荐
				</template>
			</titleVue>
			
			<view class="Recommend-View">
				<view class="Recommend-Title">
					<view class="Title" v-for="(item,index) in RecommendTitle" :key="index">
						<p :style="{color:item.color}">{{item.name}}</p>
						<span>{{item.Subtitle}}</span>
					</view>
				</view>
				
				<view class="Recommend-Product">
					<view class="Product-MaxTitle">
						<p>每日申赎</p>
						<span>财富臻选</span>
					</view>
					<view class="Product-Centent">
						<p>兴银稳添利日盈增...</p>
						<span> <uni-tag class="uni-tag" :inverted="true" text="理财" type="default" size="mini" /> <text>1.00起购</text></span>
					</view>
				</view>
				
				<view class="Recommend-Product">
					<view class="Product-MaxTitle">
						<p>每日申赎</p>
						<span>为您精选</span>
					</view>
					<view class="Product-Centent">
						<p>中银理财-稳富高...</p>
						<span><uni-tag class="uni-tag" :inverted="true" text="理财" type="default"  size="mini" /> <text>1.00起购</text></span>
					</view>
				</view>
			</view>
			
		</view>
		<view class="index-Activity">
			<titleVue :LFontSize="'38'" :icon="true" IconSize="1.5">
				<template #left>
					热门活动
				</template>
			</titleVue>
			
			<view class="Activity-Box">
				<view class="MaxBanner">
					<image src="@/static/Activity-bg-1.png" mode=""></image>
				</view>
				<view class="MaxBanner">
					<view class="branch">
						<image src="@/static/Activity-bg-2.png" mode=""></image>
					</view>
					<view class="branch">
						<image src="@/static/Activity-bg-3.png" mode=""></image>
					</view>
				</view>
			</view>
		</view>
		<view class="index-Theme">
			<titleVue :icon="true" IconSize="1.5" LFontSize="38">
				<template #left>
					热议话题
				</template>
			</titleVue>
			
			<image src="../../static/Theme-bg-1.png" mode=""></image>
		</view>
		<view class="index-MyBranches">
			<titleVue :icon="true" IconSize="1.5" LFontSize="38">
				<template #left>
					热议话题
				</template>
			</titleVue>
			
			<view class="MyBranches-banner">
				<image src="@/static/MyBranches-1.png" mode=""></image>
			</view>
			
			<view class="MyBranches-Text">
				<span>立即取号</span>
				<span>外币现钞预约</span>
				<span>卡片挂失</span>
			</view>
		</view>
		<view class="index-pension">
			<titleVue :icon="true" IconSize="1.5" LFontSize="38">
				<template #left>
					个人养老金
				</template>
			</titleVue>
			
			<image src="../../static/pension-1.png" mode=""></image>
		</view>
		<view class="index-characteristic">
			<titleVue :icon="true" IconSize="1.5" LFontSize="38">
				<template #left>
					特色服务
				</template>
			</titleVue>
			
			<view class="characteristic-ListView">
				<view class="image">
					<image src="@/static/characteristic-1.png" mode=""></image>
				</view>
				<view class="ListView">
					<view class="Box">
						<image src="../../static/characteristic-icon-1.png" mode=""></image>
					</view>
					<p>跨行汇款</p>
				</view>
				<view class="ListView">
					<view class="Box">
						<image src="../../static/characteristic-icon-2.png" mode=""></image>
					</view>
					<p>买外币</p>
				</view>
			</view>
			
			<view class="characteristic-ListView">
				<view class="image">
					<image src="@/static/characteristic-2.png" mode=""></image>
				</view>
				<view class="ListView">
					<view class="Box">
						<image src="../../static/characteristic-icon-3.png" mode=""></image>
					</view>
					<p>跨行汇款</p>
				</view>
				<view class="ListView">
					<view class="Box">
						<image src="../../static/characteristic-icon-4.png" mode=""></image>
					</view>
					<p>买外币</p>
				</view>
			</view>
			
			<view class="characteristic-ListView">
				<view class="image">
					<image src="@/static/characteristic-3.png" mode=""></image>
				</view>
				<view class="ListView">
					<view class="Box">
						<image src="../../static/characteristic-icon-5.png" mode=""></image>
					</view>
					<p>跨行汇款</p>
				</view>
				<view class="ListView">
					<view class="Box">
						<image src="../../static/characteristic-icon-6.png" mode=""></image>
					</view>
					<p>买外币</p>
				</view>
			</view>
			
			<view class="characteristic-ListView">
				<view class="image">
					<image src="@/static/characteristic-4.png" mode=""></image>
				</view>
				<view class="ListView">
					<view class="Box">
						<image src="../../static/characteristic-icon-7.png" mode=""></image>
					</view>
					<p>跨行汇款</p>
				</view>
				<view class="ListView">
					<view class="Box">
						<image src="../../static/characteristic-icon-8.png" mode=""></image>
					</view>
					<p>买外币</p>
				</view>
			</view>
		
			<view class="characteristic-modular">
				<image src="../../static/characteristic-5.png" mode=""></image>
				<view class="ListView" v-for="(item,index) in CharacteristicModularList " :key="index">
					<view class="Box">
						<image :src="`../../static/characteristic-icon-${index + 9}.png`" mode=""></image>
					</view>
					<p>{{item}}</p>
				</view>
			</view>
		</view>
		<view class="index-School">
			<titleVue :icon="true" IconSize="1.5" LFontSize="38">
				<template #left>
					消防学堂
				</template>
			</titleVue>
			<image src="../../static/School-1.png" mode=""></image>
		</view>
		<view class="index-FooterView">
			<view class="ListView">
				+定制个性化首页
			</view>
			<view class="ListView-Prompt">
				<span>隐私设置</span>
				<span>关于我们</span>
				<span style="border: none;">投诉渠道</span>
			</view>
		</view>
		 
	</view>
</template>

<script>
	import occupyVuew from '@/components/occupy.vue'
	import ListView from '@/components/ListView.vue'
	import titleVue from '@/components/titleVue.vue'
	import SeachTitle from '@/components/SeachTitle.vue'
	import HeadTitleVue from '../../components/HeadTitle.vue'

	export default {
		data() {
			return {
				IconView:['扫一扫','活钱宝','转账','账户管理'],
				ViewList:[
					{name:'账号转账',icon:'../../static/ListView-icon-4.png'},
					{name:'手机号转账',icon:'../../static/ListView-icon-11.png'},
					{name:'基金',icon:'../../static/ListView-icon-7.png'},
					{name:'理财',icon:'../../static/ListView-icon-5.png'},
					{name:'贷款',icon:'../../static/ListView-icon-2.png'},
					{name:'存款管理',icon:'../../static/ListView-icon-1.png'},
					{name:'结汇购汇',icon:'../../static/ListView-icon-3.png'},
					{name:'生活缴费',icon:'../../static/ListView-icon-8.png'},
					{name:'跨境汇款',icon:'../../static/ListView-icon-9.png'},
					{name:'更多',icon:'../../static/ListView-icon-10.png'},
				],
				RecommendTitle:[
					{name:'726.22',Subtitle:'美元(USD)',color:'#000'},
					{name:'786.53 ↑',Subtitle:'黄金(AU)',color:'#cf0733'},
					{name:'3373.03 ↓',Subtitle:'上证指数',color:'#097653'}
				],
				ScrollTop:0,
				CharacteristicModularList:['中银基金','中银证券','中银三星','中银保险','中银消费'],
				TitleMenu:[
					{name:'版本',image:'../../static/boc_folder_title_login_white_next.png'},
					{name:'客服',image:'../../static/boc_folder_title_white_service.png'},
					{name:'消息',image:'../../static/boc_folder_title_white_msg.png'}
				],
				TitleMenuBlack:[
					{name:'版本',image:'../../static/boc_folder_title_login_next.png'},
					{name:'客服',image:'../../static/boc_folder_title_service.png'},
					{name:'消息',image:'../../static/boc_folder_title_msg.png'}
				],
				Icon:'../../static/boc_folder_title_login_white_pre.png',
				Iconblack:'../../static/boc_folder_title_login_pre.png',
				token:''
			}
		},
		components:{
			occupyVuew,
			ListView,
			titleVue,
			SeachTitle,
			HeadTitleVue,
			
		},
		onPageScroll(Scroll) {
			// 获取页面滚动值
			this.ScrollTop = Scroll.scrollTop
		},
		methods:{
			getAccount(){
				// 获取登录信息
				this.token = uni.getStorageSync('account')
			},
			Next(index){
				console.log(!uni.getStorageSync('account').token);
				if(!uni.getStorageSync('account').token){
					return
				}
				
				index === 0 ? uni.navigateTo({
					url:'/pages/AccountTransfer/AccountTransfer'
				}) : ''
				index === 1 ? uni.navigateTo({
					url:'/pages/transferPhone/transferPhone'
				}) : ''
				// 跳转贷款页面
				index === 4 ? uni.navigateTo({
					url:'/pages/loan/loan'
				}) : ''
			},
			IconViewIndex(index){
				console.log(index);
				if(!uni.getStorageSync('account').token){
					return
				}
				// 跳转转账页面
				index === 2 ? uni.navigateTo({
					url:'/pages/transfer/transfer'
				}):''
				index === 3 ? uni.navigateTo({
					url:'/pages/AccountOverview/AccountOverview'
				}):''
			}
		},
		created(){
			// 调用登录
			this.getAccount()
		},
		// onShow() {
		// 	// 退出登录
		// 	uni.getStorageSync('account') === ''
		// 	this.getAccount()
		// },
	}
</script>

<style scoped lang="scss">
	.index{
		width: 100vw;
		padding-bottom: 50rpx;
		background: url('../../static/index-bg-1.png') no-repeat;
		background-size:100% 500rpx;
		.index-Scroll-Title{
			width: 100vw;
			background-color: #fff;
			position: fixed;
			top: 0;
			z-index: 999;
			padding-bottom: 20rpx;
		}
		.index-IconView{
			display: flex;
			padding: 30rpx;
			margin-top: 20rpx;
			justify-content: space-between;
			.IconView{
				display: flex;
				flex-wrap: wrap;
				align-items: center;
				justify-content: center;
				image{
					width: 70rpx;
					height: 70rpx;
				}
				span{
					margin-top: 20rpx;
					text-align: center;
					width: 100%;
					color: #fff;
					font-size: 28rpx;
				}
			}
		}
		.index-ListView{
			margin: 0 auto;
			margin-top: 130rpx;
			background-color: #fff;
		}
		.index-Notice{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			display: flex;
			justify-content: space-between;
			align-items: center;
			padding: 20rpx;
			background-color: #f9f9f9;
			border-radius: 10rpx;
			.Notice-Text{
				display: flex;
				align-items: center;
				font-size: 28rpx;
				line-height: 45rpx;
				image{
					width: 90rpx;
					height: 90rpx;
					margin-right: 30rpx;
				}
			}
			.IconRight{
				width: 50rpx;
				height: 50rpx;
			}
		}
		.index-banner{
			width: 90%;
			margin: 0 auto;
			margin-top: 30rpx;
			height: 170rpx;
			swiper{
				width: 100%;
				height: 100%;
				::v-deep.uni-swiper-dot{
					width: 10rpx;
					height: 5rpx;
					border-radius: 10rpx;
					background-color: #f7f7f7;
				}
				::v-deep.uni-swiper-dot-active{
					width: 20rpx;
					height: 5rpx;
					border-radius: 10rpx;
					background-color: #fff;
				}
				swiper-item{
					image{
						width: 100%;
						height: 170rpx;
					}
				}
				
			}
		}
		.index-recommend{
			width: 90%;
			margin: 0 auto;
			.Recommend-View{
				background-color: #fcefe2;
				border-radius: 10rpx;
				padding: 20rpx;
				.Recommend-Title{
					background-color: #fff;
					margin: 0 auto;
					display: flex;
					align-items: center;
					justify-content: space-between;
					padding: 20rpx;
					border-bottom: 1px solid #ddd;
					.Title{
						line-height: 45rpx;
						p{
							font-size: 30rpx;
							font-weight: bold;
						}
						span{
							font-size: 25rpx;
							color: #666;
						}
					}
				}
				.Recommend-Product{
					background-color: #fff;
					display: flex;
					justify-content: space-between;
					padding: 20rpx;
					line-height: 50rpx;
					.Product-MaxTitle{
						flex: 1;
						p{
							font-size: 45rpx;
							color: #ca103f;
							font-weight: bold;
						}
						span{
							color: #666;
							font-size: 28rpx;
						}
					}
					.Product-Centent{
						width: 55%;
						p{
							font-size: 35rpx;
							color: #000;
							font-weight: bold;
						}
						span{
							color: #666;
							font-size: 28rpx;
							.uni-tag{
								font-size: 20rpx;
								margin-right: 10rpx;
							}
						}
					}
				}
			}
			
		}
		.index-Activity{
			width: 90%;
			margin: 0 auto;
			.Activity-Box{
				width: 100%;
				display: flex;
				justify-content: space-between;
				.MaxBanner{
					width: 49%;
					image{
						width: 100%;
						height: 400rpx;
					}
					.branch{
						width: 100%;
						height: 48%;
						margin-bottom: 10rpx;
						image{
							width: 100%;
							height: 100%;
						}
					}
				}
			}
		}
		.index-Theme{
			width: 90%;
			margin: 0 auto;
			image{
				width: 100%;
				height: 310rpx;
			}
		}
		.index-MyBranches{
			width: 90%;
			margin: 0 auto;
			.MyBranches-banner{
				width: 100%;
				image{
					width: 100%;
					height: 180rpx;
					border: 1px solid #ddd;
					border-radius: 20rpx; 
				}
			}
			.MyBranches-Text{
				border: 1px solid #ddd;
				width: 90%;
				margin: 0 auto;
				margin-top: -20rpx;
				padding: 35rpx;
				display: flex;
				align-items: center;
				justify-content: space-between;
				font-size: 28rpx;
				color: #2361ac;
				
			}
		}
		.index-pension{
			width: 90%;
			margin: 0 auto;
			image{
				width: 100%;
				height: 180rpx;
			}
		}
		.index-characteristic{
			width: 90%;
			margin: 0 auto;
			display: flex;
			flex-wrap: wrap;
			justify-content: space-between;
			.characteristic-ListView{
				width: 49%;
				display: flex;
				flex-wrap: wrap;
				margin-bottom: 20rpx;
				background-color: #fffbf8;
				border-radius: 20rpx;
				.image{
					width: 100%;
					display: flex;
					justify-content: space-between;
					image{
						width: 100%;
						height: 150rpx;
					}
				}
				.ListView{
					width: 50%;
					margin-top: 10rpx;
					.Box{
						width: 100%;
						display: flex;
						flex-wrap: wrap;
						justify-content: center;
						image{
							width: 50rpx;
							height: 50rpx;
						}
					}
					p{
						text-align: center;
						width: 100%;
						font-size: 25rpx;
						margin-top: 5rpx;
						margin-bottom: 20rpx;
					}
				}
			}
			.characteristic-modular{
				width: 100%;
				margin-top: 10rpx;
				display: flex;
				flex-wrap: wrap;
				justify-content: space-between;
				background-color: #fcf8f7;
				border-radius: 20rpx;
				image{
					width: 100%;
					height: 180rpx;
				}
				.ListView{	
					padding: 15rpx;
					.Box{
						width: 100%;
						display: flex;
						flex-wrap: wrap;
						justify-content: center;
						image{
							width: 50rpx;
							height: 50rpx;
						}
					}
					p{
						text-align: center;
						width: 100%;
						font-size: 25rpx;
						margin-top: 5rpx;
					}
				}
			}
		}
		.index-School{
			width: 90%;
			margin: 0 auto;
			image{
				width: 100%;
				height: 180rpx;
			}
		}
		.index-FooterView{
			display: flex;
			flex-wrap: wrap;
			justify-content: center;
			margin-top: 30rpx;
			.ListView{
				padding:10rpx 25rpx;
				border: 1px solid;
				border-radius: 50rpx;
				font-size: 28rpx;
			}
			.ListView-Prompt{
				width: 100%;
				display: flex;
				justify-content: center;
				align-items: center;
				margin-top: 30rpx;
				span{
					display: flex;
					align-items: center;
					height:30rpx;
					border-right:1px solid #9b9b9b;
					padding: 0 20rpx;
					color: #276aa8;
					font-size: 28rpx;
				}
			}
		}
	}
</style>
