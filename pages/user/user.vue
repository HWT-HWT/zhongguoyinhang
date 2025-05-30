<template>
	<view class="user" v-if="token">
		<view class="user-title">
			<occupyVue :hight="'90rpx'"></occupyVue>
			<HeadTitleVue :menu='TitleMenu' :Icon='Icon' :isTrue="false" >
				退出
			</HeadTitleVue>
		</view>
		<view class="user-Scroll-Title" v-if="!ScrollTop == 0" :style="{opacity:`${ScrollTop / 100 }`}">
			<occupyVue :hight="'90rpx'"></occupyVue>
			<HeadTitleVue :menu='TitleMenuBlack' :Icon='IconBlack' TextColor='#000'  :isTrue="false" >
				退出
			</HeadTitleVue>
		</view>
		<view class="user-header">
			<image src="@/static/fuzai_icon_default_setting.png" mode=""></image>
			<view class="header-text">
				<p>下午好 , 马*超</p>
				<span>上次登录:{{date}}</span>
			</view>
		</view>
		<view class="user-ToDoList">
			<view class="ToDoImage">
				<image src="@/static/bg_mine_todo.png" mode=""></image>
				<view class="Sum" style="width: 35rpx;">
					2
				</view>
			</view>
			<view class="ToDoText">
				<image src="@/static/abc_scrubber_control_to_pressed_mtrl_005.png" mode=""></image> 近7日暂无事项,点击查看更多
			</view>
			<image src="@/static/upsdk_payment_right.webp" mode=""></image>
		</view>
		<view class="user-List">
			<ListViewVue :listTitle="UserList" :Pad="'20rpx 15rpx'" @ClickNext='Next'></ListViewVue>
		</view>
		<view class="user-MyAssets">
			<TitleVue LFontSize="38" >
				<template #left >
					<view @click="ClickEye">
						我的资产
						<image v-if="!MyAssetsEye" src="../../static/icon_folder_eye_open.png" mode=""></image>
						<image v-else src="../../static/icon_folder_eye_close.png" mode=""></image>
					</view>
				</template>
			</TitleVue>
			
			<view class="MyAssets-View">
				<view class="Row">
					<view class="ListView" @click="GoAssets">资产 <image src="@/static/upsdk_payment_right.webp" mode=""></image> </view>
					<span>{{MyAssetsEye ? '******' : '51,602.48'}}</span>
				</view>
				<view class="Row">
					<view class="ListView">昨日收益 <image src="@/static/upsdk_payment_right.webp" mode=""></image> </view>
					<span>{{MyAssetsEye ? '******' : '暂无收益'}}</span>
				</view>
			</view>
		</view>
		<view class="user-MyAssets">
			<TitleVue LFontSize="38">
				<template #left>
					我的收支
				</template>
			</TitleVue>
			
			<view class="MyAssets-View">
				<view class="Row">
					<view class="ListView">收入</view>
					<span>{{MyAssetsEye ? '******' : '5,850.25'}}</span>
				</view>
				<view class="Row">
					<view class="ListView">支出</view>
					<span>{{MyAssetsEye ? '******' : '0.00'}}</span>
				</view>
			</view>
		</view>
		<view class="user-Outlets-title">
			<TitleVue LFontSize="38" :icon="true" IconSize="2">
				<template #left>
					我的贷款
				</template>
			</TitleVue>
		</view>
		
		<view class="user-Outlets-loan" @click="GoLoan">
			<view class="p">贷款本金总余额(人民币元) <image src="@/static/boc_finance_gray_help.png" mode=""></image> </view>
			<span>1,100,000.00</span>
		</view>
		
		<!-- <view class="user-Outlets-title">
			<TitleVue LFontSize="38" :icon="true" IconSize="2">
				<template #left>
					我的网点
				</template>
			</TitleVue>
		</view>
		<view class="user-Outlets">
			<view class="Outlets-Row">
				<view class="title">中国银行广佛智城... <image src="@/static/upsdk_payment_right.webp"></image> </view>
				<view class="centent">佛山市南海区岭南路85号a5座</view>
				<p>距您 <span class="FW">1.5km</span> 离您最近</p>
			</view>
			<view class="Outlets-Btn">
				<view class="btn">
					<image src="@/static/user-icon-3.png" mode=""></image>
					<p>导航</p>
				</view>
				<view class="btn">
					<image src="@/static/user-icon-4.png" mode=""></image>
					<p>电话</p>
				</view>
			</view>
			<view class="Outlets-Footer">
				<view v-for="(item,index) in OutletsFooter" :key="item" :style="{borderRight:index === 2 ? 'none':'1px solid #ddd'}">
					{{item}}
				</view>
			</view>
		</view> -->
		<view class="user-more">
			<TitleVue LFontSize="38">
				<template #left>
					 更多服务
				</template>
			</TitleVue>
			<view class="More-Row">
				<p>个人信用报告</p>
				<image src="../../static/user-image-1.png" mode=""></image>
			</view>
			<view class="More-Row">
				<p>我的分享</p>
				<image src="../../static/user-image-2.png" mode=""></image>
			</view>
		</view>
		<view class="user-footer">
			<view class="Outlets-Footer">
				<view v-for="(item,index) in Footer" :key="item" :style="{borderRight:index === 2 ? 'none':'1px solid #888'}">
					{{item}}
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue';
	import HeadTitleVue from '../../components/HeadTitle.vue';
	import ListViewVue from '../../components/ListView.vue';
	import TitleVue from '@/components/titleVue.vue'
	export default {
		data() {
			return {
				TitleMenu:[
					{name:'设置',image:'../../static/boc_communication_set-white.png'},
					{name:'客服',image:'../../static/boc_folder_title_white_service.png'},
					{name:'消息',image:'../../static/boc_folder_title_white_msg.png'}
				],
				TitleMenuBlack:[
					{name:'设置',image:'../../static/boc_communication_set.png'},
					{name:'客服',image:'../../static/boc_folder_title_service.png'},
					{name:'消息',image:'../../static/boc_folder_title_msg.png'}
				],
				Icon:'../../static/boc_en_logout.png',
				IconBlack:'../../static/boc_en_logout_gray.png',
				ScrollTop:0,
				UserList:[
					{name:'我的账户',num:'1'},
					{name:'我的权益',num:'5'},
					{name:'我的积分',icon:'../../static/user-icon-1.png'},
					{name:'我的游戏',icon:'../../static/user-icon-2.png'}
				],
				MyAssetsEye:false,
				OutletsFooter:['立即取号','外币现钞预约','卡片挂失'],
				Footer:['隐私政策','关于我们','投诉渠道'],
				date:'',
				token:''
			};
		},
		components:{
			occupyVue,
			HeadTitleVue,
			ListViewVue,
			TitleVue
		},
		onPageScroll(Scroll) {
			this.ScrollTop = Scroll.scrollTop
		},
		methods:{
			ClickEye(){
				this.MyAssetsEye = !this.MyAssetsEye
			},
			Next(index){
				index === 0 ? uni.navigateTo({
					url:'/pages/AccountOverview/AccountOverview'
				}) : ''
			},
			GoAssets(){
				uni.navigateTo({
					url:'/pages/assets/assets'
				})
			},
			GoLoan(){
				uni.navigateTo({
					url:'/pages/loan/loan?id=4'
				})
			}
		},
		onShow() {
			this.token = uni.getStorageSync('account')
			if(!uni.getStorageSync('account')){
				uni.navigateTo({
					url:'/pages/gesture/gesture'
				})
			}
		},
		created() {
			this.date = uni.getStorageSync('OldDate')
		}
	}
</script>

<style lang="scss">
	.user{
		width: 100vw;
		background: url('@/static/user-bg-1.png')no-repeat;
		background-size: 100% 450rpx;
		padding-bottom:50rpx;
		background-color: #fff;
		.user-Scroll-Title{
			background-color: #fff;
			position: fixed;
			top: 0;
			z-index: 999;
			padding-bottom: 20rpx;
		}
		.user-header{
			display: flex;
			
			align-items: center;
			padding: 30rpx;
			image{
				width: 130rpx;
				height: 130rpx;
				margin: 0 30rpx;
			}
			.header-text{
				color: #fff;
				line-height: 50rpx;
				p{
					font-size: 35rpx;
				}
				span{
					font-size:22rpx;
				}
			}
		}
		.user-ToDoList{
			width: 90%;
			margin: 0 auto;
			display: flex;
			align-items: center;
			justify-content: space-between;
			margin-top: 140rpx;
			.ToDoImage{
				background-color: #f7f7f7;
				padding: 10rpx 5rpx;
				display: flex;
				align-items: center;
				justify-content: center;
				border-radius: 10rpx;
				transform: scale(0.8);
				image{
					width:60rpx;
					height:28rpx;
				}
				.Sum{
					background-color: #d60236;
					display: flex;
					align-items: center;
					justify-content: center;
					color: #fff;
					font-size: 25rpx;
					margin:0 10rpx;
					padding: 5rpx;
					border-radius: 5rpx;
				}
			}
			.ToDoText{
				flex: 1;
				display: flex;
				align-items: center;
				font-size: 25rpx;
				image{
					width: 10rpx;
					height: 10rpx;
					margin: 0 12rpx;
				}
			}
			image{
				width: 50rpx;
				height: 50rpx;
			}
		}
		.user-List{
			width: 90%;
			margin: 0 auto;
			margin-top: 40rpx;
			margin-top: 40rpx;
			box-shadow: 0 0 10rpx 1rpx rgba(0, 0, 0, .1);
			border-radius: 10rpx;
			
		}
		.user-MyAssets{
			width: 90%;
			margin: 0 auto;
			display: flex;
			flex-wrap: wrap;
			align-items: center;
			image{
				width: 40rpx;
				height: 30rpx;
				margin-left: 10rpx;
			}
			.MyAssets-View{
				width: 100%;
				background: url('@/static/user-bg-2.png');
				background-size: 100% 100%;
				border-radius: 10rpx;
				display: flex;
				justify-content: space-between;
				box-shadow: 0 0 10rpx 1rpx rgba(0, 0, 0, .1);
				margin-top: 20rpx;
				.Row{
					padding: 30rpx;
					font-size: 33rpx;
					.ListView{
						width: 100%;
						line-height: 80rpx;
						display: flex;
						align-items: center;
						image{
							width: 45rpx;
							height: 45rpx;
						}
					}
					span{
						width: 100%;
					}
				}
			}
		}
		.user-Outlets-title{
			width: 90%;
			margin: 0 auto;
		}
		.user-Outlets-loan{
			width: 80%;
			margin: 0 auto;
			margin-top: 20rpx;
			background: url('@/static/user-loan-1.png');
			display: flex;
			flex-wrap: wrap;
			padding:30rpx 40rpx;
			align-items: center;
			justify-content: center;
			font-size: 28rpx;
			border-radius:20rpx; 
			border: 1px solid #ddd;
			.p{
				display: flex;
				align-items: center;
				justify-content: center;
				width: 100%;
				text-align: center;
				image{
					width: 28rpx;
					height: 28rpx;
					margin-top: 10rpx;
					margin-left: 10rpx;
				}
			}
			span{
				font-weight: bold;
				font-size: 38rpx;
				margin-top: 10rpx;
			}
		}
		.user-Outlets{
			width: 80%;
			margin: 0 auto;
			margin-top: 20rpx;
			background: url('@/static/user-bg-3.png');
			display: flex;
			flex-wrap: wrap;
			padding:30rpx 40rpx;
			align-items: center;
			font-size: 28rpx;
			border-radius: 30rpx 30rpx 20rpx 20rpx; 
			border: 1px solid #ddd;
			.Outlets-Row{
				width: 60%;
				.title{
					display: flex;
					flex-wrap: wrap;
				}
				image{
					width: 45rpx;
					height: 45rpx;
				}
				.centent{
					color: #666;
					margin: 10rpx 0;
				}
				.FW{
					font-weight: bold;
					margin: 0 10rpx;
				}
			}
			.Outlets-Btn{
				flex: 1;
				display: flex;
				flex-wrap: wrap;
				justify-content: center;
				margin-left:30rpx;
				.btn{
					margin: 0 20rpx;
					image{
						width: 60rpx;
						height: 60rpx;
					}
					p{
						text-align: center;
						font-size: 25rpx;
						width: 100%;
					}
				}
			}
			.Outlets-Footer{
				width: 100%;
				display: flex;
				justify-content: space-between;
				border-top: 1rpx solid #ddd;
				padding-top: 25rpx;
				margin-top: 30rpx;
				view{
					padding: 0 30rpx;
					border-right: 1px solid #ddd;
					color: #2664b3;
					font-size: 28rpx;
				}
			}
		}
		.user-more{
			width: 90%;
			margin: 0 auto;
			display: flex;
			flex-wrap: wrap;
			.More-Row{
				width: 48%;
				flex: 1;
				margin: 5rpx;
				border: 10px solid #f6f6f6;
				font-size: 35rpx;
				border-radius: 20rpx;
				font-weight: bold;
				display: flex;
				justify-content: center;
				flex-wrap: wrap;
				p{
					width: 100%;
					padding:25rpx;
				}
				image{
					width: 90%;
					height: 300rpx;
					padding-bottom: 20rpx;
				}
			}
		}
		.user-footer{
			.Outlets-Footer{
				display: flex;
				justify-content: center;
				padding-top: 25rpx;
				margin-top: 30rpx;
				view{
					padding: 0 30rpx;
					color: #2664b3;
					font-size: 28rpx;
				}
			}
		}
	}
</style>
