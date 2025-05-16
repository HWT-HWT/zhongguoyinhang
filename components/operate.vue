<template>
	<view class="operate">
		<loanTitleVue :name="name" :TitleImage='TitleImage' :rigthIcon='rigthIcon' :Scollor="TopTitle"></loanTitleVue>
		<view class="operate-List">
			<ListViewVue :listTitle="loanSetting" FontSize="25rpx" sizi='60rpx' width="25%" Pad='30rpx 0'></ListViewVue>
		</view>
		<view class="operate-product">
			<view class="product">
				<titleVue LFontSize="38">
					<template #left>
							优选产品
					</template>
				</titleVue>
				<image src="../static/operate-image-1.png" mode=""></image>
				<image src="../static/operate-image-2.png" mode=""></image>
				<image src="../static/operate-image-3.png" mode=""></image>
			</view>
		</view>
		<view class="operate-Zone">
			<view class="Zone">
				<titleVue LFontSize="38">
					<template #left>
							经营专区
					</template>
				</titleVue>
				<view class="Zone-Image-Text">
					<image src="../static/Zone-image-1.png" mode=""></image>
					<view class="Text">
						立即使用
					</view>
				</view>
				<view class="Zone-Image-Text">
					<image src="../static/Zone-image-2.png" mode=""></image>
					<view class="Text">
						立即使用
					</view>
				</view>
			</view>
		</view>
		<view class="operate-Huinong">
			<view class="Huinong">
				<titleVue LFontSize="38" RColor="#666">
					<template #left>
						惠农专区
					</template>
					<template #rigth>
						我是农户 同筑富裕乡村
					</template>
				</titleVue>
				<image src="@/static/Huinong-image-1.png" mode=""></image>
				<image src="@/static/Huinong-image-2.png" mode=""></image>
			</view>
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
				<p class="FW">Q:商户速贷简介?</p>
				<p><span class="FW">A:</span>商户速贷是中国银行为个体工商户、小微企业主等从事生产经营的个人客户提供的普惠金融线上对私系列贷款产...</p>
			</view>
			<view class="guide-listView" :style="{border:'none'}">
				<p  class="FW">Q:申请商户速贷有哪些条件，需要提供哪些申请材料?</p>
				<p><span class="FW">A:</span>个体工商户、小微企业主等从事生产经营的个人客户均可通过中国银行手机银行、惠如愿APP在线申请商户速贷...</p>
			</view>
		</view>
	</view>
</template>

<script>
	import loanTitleVue from './loan-Title.vue';
	import ListViewVue from './ListView.vue';
	import titleVue from './titleVue.vue';
	export default {
		name:"operate",
		data() {
			return {
				TitleImage:"../../static/back_black.png",
				rigthIcon:['../../static/boc_folder_title_service.png','../../static/icon_share_black.png'],
				loanSetting:[
					{name:'视频面谈',icon:'../../static/operate-icon-1.png'},
					{name:'贷款资金转出',icon:'../../static/operate-icon-2.png'},
					{name:'征信查询',icon:'../../static/operate-icon-3.png'},
					{name:'在线签约',icon:'../../static/operate-icon-4.png'},
					{name:'贷款记录',icon:'../../static/operate-icon-5.png'},
					{name:'额度查询',icon:'../../static/operate-icon-6.png'},
					{name:'申请进度查询',icon:'../../static/operate-icon-5.png'},
					{name:'房产估值',icon:'../../static/operate-icon-6.png'},
				],
				guideList:['商户速贷','中银速贷','更多']
			}
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
			ListViewVue,
			titleVue
		},
	}
</script>

<style lang="scss" scoped>
	.operate{
		width: 100%;
		background: url('@/static/consumption-bg-3.png') no-repeat;
		background-size:100% 400rpx ;
		background-color: #f7f7f7;
		padding-bottom: 100rpx;
		.operate-List{
			margin-top: 280rpx;
			background-color: #fff;
		}
		.operate-product{
			width: 100%;
			background-color: #fff;
			.product{
				width: 90%;
				margin: 0 auto;
				image{
					width: 100%;
					height: 230rpx;
				}
			}
		}
		.operate-Zone{
			width: 100%;
			background-color: #fff;
			.Zone{
				width: 90%;
				margin: 0 auto;
				.Zone-Image-Text{
					border-radius: 20rpx;
					image{
						width: 100%;
						height: 260rpx;
						border-radius: 20rpx 20rpx 0 0;
					}
					.Text{
						display: flex;
						align-items: center;
						justify-content: center;
						padding: 20rpx 0;
						font-size: 28rpx;
					}
				}
				
			}
		}
		.operate-Huinong{
			width: 100%;
			background-color: #fff;
			.Huinong{
				width: 90%;
				margin: 0 auto;
				image{
					width: 100%;
					height: 260rpx;
					margin-bottom: 20rpx;
				}
			}
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