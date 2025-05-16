<template>
	<view class="Card">
		<view class="Card-Title">
			<occupyVue hight="90rpx"></occupyVue>
			<HeadTitleVue :menu='TitleMenu' TextColor="#000">
				登录
			</HeadTitleVue>
		</view>
		<view class="Card-Fixed"  v-if="!ScrollTop == 0" :style="{opacity:`${ScrollTop / 100 }`}">
			<occupyVue hight="90rpx"></occupyVue>
			<HeadTitleVue :menu='TitleMenu' TextColor="#000">
				登录
			</HeadTitleVue>
		</view>
		<!-- <view class="Card-ListView">
			<p>登录查看更多信息</p>
			<view class="Login">
				去登录
			</view>
			<view class="FooterText">
				查看更多信用卡，申请享优惠 >
			</view>
		</view> -->
		<view class="Card-List">
			<ListViewVue :listTitle='ViewList' :Pad="'30rpx 0'" FontSize="25rpx"></ListViewVue>
		</view>
		<view class="Card-Image">
			<image src="@/static/Card-bg-1.png" mode=""></image>
		</view>
		<view class="Card-banner">
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item v-for="(item,index) in 5" :key="index">
					<image :src="`../../static/Card-advertisement-${index+1}.png`" mode=""></image>
				</swiper-item>
			</swiper>
		</view>
		<view class="Card-HotCard">
			<titleVue LFontSize="38" :icon="true" IconSize="1.5">
				<template #left>
					热卡精彩
				</template>
			</titleVue>
			<view class="Card-Flex">
				<image src="@/static/HotCard-image-1.png" style="width: 65%;" mode=""></image>
				<image src="@/static/HotCard-image-2.png" style="width: 33%;" mode=""></image>
				<image src="@/static/HotCard-image-3.png" style="width: 33%;" mode=""></image>
				<image src="@/static/HotCard-image-4.png" style="width: 30%;" mode=""></image>
				<image src="@/static/HotCard-image-5.png" style="width: 33%;" mode=""></image>
			</view>
		</view>
		<view class="Card-Power">
			<titleVue LFontSize="38">
				<template #left>
					权益领取
				</template>
			</titleVue>
			
			<view class="PowerView">
				<image src="@/static/Power-image-1.png" mode=""></image>
				<view class="View" v-for="(item,index) in PowerList" :key="index">
					<image :src="item.image" mode=""></image>
					<view class="ViewText">
						<p>{{item.name}}</p>
						<span>{{item.SubName}}</span>
					</view>
				</view>
			</view>
		</view>
		<view class="Card-Cheap">
			<titleVue LFontSize="38">
				<template #left>
					特惠在身边
				</template>
			</titleVue>
			<view class="Cheap-View">
				<image v-for="(item,index) in 4" :key="index" :src="`../../static/Cheap-image-${index+1}.png`" mode=""></image>
			</view>
		</view>
		<view class="Card-Live">
			<titleVue LFontSize="38">
				<template #left>
					分期生活
				</template>
			</titleVue>
			<view class="Card-Flex">
				<image src="@/static/Card-Live-image-1.png" style="width: 64%;" mode=""></image>
				<image src="@/static/Card-Live-image-2.png" style="width: 34%;" mode=""></image>
				<image src="@/static/Card-Live-image-3.png" style="width: 32%;" mode=""></image>
				<image src="@/static/Card-Live-image-4.png" style="width: 32%;" mode=""></image>
				<image src="@/static/Card-Live-image-5.png" style="width: 32%;" mode=""></image>
			</view>
		</view>
		<view class="Card-Zone">
			<titleVue LFontSize="38">
				<template #left>
					特色专区
				</template>
			</titleVue>
			
			<image src="@/static/Card-Zone-1.png" mode=""></image>
			<image src="@/static/Card-Zone-2.png" mode=""></image>
		</view>
	</view>
</template>

<script>
	import HeadTitleVue from '../../components/HeadTitle.vue';
	import occupyVue from '../../components/occupy.vue';
	import ListViewVue from '../../components/ListView.vue';
	import titleVue from '../../components/titleVue.vue';
	export default {
		data() {
			return {
				TitleMenu:[
					{name:'客服',image:'../../static/boc_folder_title_service.png'}
				],
				ViewList:[
					{name:'余额转出',icon:'../../static/Card-icon-1.png'},
					{name:'额度管理',icon:'../../static/Card-icon-2.png'},
					{name:'积分',icon:'../../static/Card-icon-3.png'},
					{name:'立即还款',icon:'../../static/Card-icon-4.png'},
					{name:'信用卡申请',icon:'../../static/Card-icon-5.png'},
					{name:'一键绑卡',icon:'../../static/Card-icon-6.png'},
					{name:'年费/卡信息',icon:'../../static/Card-icon-7.png'},
					{name:'数字信用卡',icon:'../../static/Card-icon-8.png'},
					{name:'卡片激活',icon:'../../static/Card-icon-9.png'},
					{name:'更多',icon:'../../static/Card-icon-10.png'},
				],
				ScrollTop:0,
				PowerList:[
					{name:'点击享权',SubName:'财富私行卡',image:'../../static/Power-image-2.png'},
					{name:'点击享权',SubName:'长城You卡',image:'../../static/Power-image-3.png'},
					{name:'查看权益',SubName:'消费达标...',image:'../../static/Power-image-4.png'},
					{name:'查看权益',SubName:'其他热门...',image:'../../static/Power-image-5.png'}
				]
			};
		},
		components:{
			HeadTitleVue,
			occupyVue,
			ListViewVue,
			titleVue
		},
		onPageScroll(Scroll) {
			this.ScrollTop = Scroll.scrollTop
		}
	}
</script>

<style lang="scss" scoped>
	.Card{
		width: 100vw;
		padding-bottom: 50rpx;
		.Card-Fixed{
			width: 100%;
			position: fixed;
			background-color: #fff;
			z-index: 999;
			top: 0;
			padding-bottom: 20rpx;
		}
		.Card-ListView{
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
		.Card-List{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
		}
		.Card-Image{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			image{
				width: 100%;
				height: 150rpx;
			}
		}
		.Card-banner{
			width: 90%;
			margin: 0 auto;
			margin-top: 40rpx;
			height: 170rpx;
			swiper{
				width: 100%;
				height: 100%;
				/deep/.uni-swiper-dot{
					width: 10rpx;
					height: 5rpx;
					border-radius: 10rpx;
					background-color: #f7f7f7;
				}
				/deep/.uni-swiper-dot-active{
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
		.Card-HotCard{
			width: 90%;
			margin: 0 auto;
			.Card-Flex{
				width: 100%;
				display: flex;
				flex-wrap: wrap;
				justify-content: space-between;
				image{
					margin-bottom: 20rpx;
					height: 300rpx;
				}
			}
		}
		.Card-Power{
			width: 90%;
			margin: 0 auto;
			.PowerView{
				display: flex;
				flex-wrap: wrap;
				justify-content: space-between;
				box-shadow: 0 0 10rpx 1rpx rgba(0, 0, 0, .1);
				border-radius: 20rpx;
				padding-bottom: 20rpx;
				image{
					width: 100%;
					height: 140rpx;
				}
				.View{
					margin-top: 20rpx;
					image{
						width: 140rpx;
						height: 120rpx;
					}
					.ViewText{
						line-height: 40rpx;
						text-align: center;
						
						p{
							font-size: 30rpx
						}
						span{
							font-size: 25rpx;
						}
					}
				}
			}
		}
		.Card-Cheap{
			width: 90%;
			margin: 0 auto;
			.Cheap-View{
				width: 100%;
				display: flex;
				flex-wrap:wrap;
				justify-content: space-between;
				image{
					width: 49%;
					height: 180rpx;
					margin-bottom:15rpx ;
				}
			}
		}
		.Card-Live{
			width: 90%;
			margin: 0 auto;
			.Card-Flex{
				width: 100%;
				display: flex;
				flex-wrap: wrap;
				justify-content: space-between;
				image{
					margin-bottom: 20rpx;
					height: 300rpx;
				}
			}
		}
		.Card-Zone{
			width: 90%;
			margin: 0 auto;
			display: flex;
			flex-wrap: wrap;
			justify-content: space-between;
			image{
				width: 49%;
				height: 240rpx;
			}
		}
	}
</style>