<template>
	<view class="assist-Learning">
		<loanTitleVue :name="name" :TitleImage='TitleImage' :rigthIcon='rigthIcon' :Scollor="TopTitle"></loanTitleVue>
		<view class="assist-Learning-product">
			<view class="product">
				<titleVue LFontSize="38">
					<template #left>
							优选产品
					</template>
				</titleVue>
				<image src="../static/assist-Learning-image-1.png" mode=""></image>
			</view>
		</view>
		<view class="assist-Learning-recommend">
			<view class="recommend">
				<titleVue LFontSize="38" RColor="#888">
					<template #left>
							为您推荐
					</template>
					<template #rigth>
						我是学生 助我梦想启航
					</template>
				</titleVue>
				<image src="../static/recommend-image-1.png" mode=""></image>
				<image src="../static/recommend-image-2.png" mode=""></image>
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
				<p class="FW">Q:国家助学贷款额度</p>
				<p><span class="FW">A:</span>学生应根据实际情况申请国家助学贷款额度，全日制普通本专科学生(含第二学士学位、高职学生、预科生)每...</p>
			</view>
			<view class="guide-listView" :style="{border:'none'}">
				<p  class="FW">Q:国家助学贷款利率</p>
				<p><span class="FW">A:</span>国家助学贷款利率按照同期同档次贷款市场报价利率(LPR)减70个基点执行...</p>
			</view>
		</view>
	</view>
</template>

<script>
	import loanTitleVue from './loan-Title.vue';
	import titleVue from './titleVue.vue';
	export default {
		name:"assist-Learning",
		data() {
			return {
				TitleImage:"../../static/back_black.png",
				rigthIcon:['../../static/boc_folder_title_service.png','../../static/icon_share_black.png'],
				guideList:['国家助学贷款','商业助学贷款','个人留学贷款','更多']
			};
		},
		components:{
			loanTitleVue,
			titleVue
		},
		props:{
			name:{
				type:String
			},
			TopTitle:{
				type:Number
			}
		}
	}
</script>

<style lang="scss" scoped>
	.assist-Learning{
		width: 100%;
		background: url('@/static/consumption-bg-4.png') no-repeat;
		background-size:100% 400rpx ;
		background-color: #f7f7f7;
		padding-bottom: 100rpx;
		.assist-Learning-product{
			width: 100%;
			background-color: #fff;
			margin-top: 250rpx;
			.product{
				width: 90%;
				margin: 0 auto;
				image{
					width: 100%;
					height: 265rpx;
				}
			}
		}
		.assist-Learning-recommend{
			width: 100%;
			background-color: #fff;
			.recommend{
				width: 90%;
				margin: 0 auto;
				image{
					width: 100%;
					height: 200rpx;
					margin-top: 20rpx;
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
					padding:10rpx 20rpx;
					background-color: #f5eadd;
					border-radius: 10rpx;
					color: #7d532a;
					margin: 0 10rpx;
					font-size: 23rpx;
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