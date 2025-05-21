<template>
	<view class="datalis">
		<view class="Transaction-details-title">
			<loanTitleVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' :name='"还款计划"' :Scollor="scrollTop" ></loanTitleVue>
		</view>
		<view class="datalis-tisi">
			还款方式:按月本息 到期还本
		</view>
		<view class="datalis-date">
			<span>共30期</span>
			<span>单位:人民币元</span>
		</view>
		<view>
			<YSteps lineNum='0' color='#fff' backgroundColor='#c3c3c3' :infoList='list'></YSteps>
		</view>
	</view>
</template>

<script>
	import loanTitleVue from '@/components/loan-Title.vue';
	import YSteps from '@/components/Y-Steps/Y-Steps.vue'
	export default {
		data() {
			return {
				TitleImage:"../../static/back_black.png",
				rigthIcon:['../../static/boc_folder_title_service.png'],
				list: [
                        {
							
							time: '2024/07/21',
                            date: '￥2,925.33',
                            info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
                        },
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
						{
							
							time: '2024/07/21',
						    date: '￥2,925.33',
						    info: '含本金0.00 | 利息2,925.33',
							over: '已结清'
						},
                    ],
					Zzclist:[
						{id:1,name:'全部',active:false},
						{id:2,name:'代还款',active:false},
						{id:3,name:'已还款',active:false},
						{id:4,name:'欠款',active:false}
					],
					istrue:false,
					titleName:'全部',
					zzcId:'',
					scrollTop:0
			};
				
		},
		components:{
			YSteps,
			loanTitleVue
		},
		methods:{
			zzcBtn(id,name){
				this.Zzclist.map(item=>item.active=false)
				this.Zzclist.find(item=>item.id === id).active = !this.Zzclist.find(item=>item.id === id).active
				setTimeout(()=>{
					this.istrue = false
				},200)
				this.titleName = name 
				this.zzcId = id
			},
			zzcIsTrue(){
				this.istrue = !this.istrue
			},
			onPageScroll(Scroll) {
				this.scrollTop =  Scroll.scrollTop
			},
		},
	}
</script>

<style lang="scss" scoped>
	.datalis{
		width: 100%;
		min-height: 100vh;
		background-color: #f4f4f4;
		.Transaction-details-title{
			background-color: #fff;
		}
		.datalis-tisi{
			padding: 20rpx;
			background-color: #fff0ff;
			font-size: 25rpx;
		}
		.datalis-date{
			display: flex;
			justify-content: space-between;
			margin: 20rpx;
			font-size: 28rpx;
		}
		.datalis-title{
			width: 90%;
			display: flex;
			justify-content: space-between;
			margin: 0 auto;
			font-size: 30rpx;
			span{
				margin-top: 28rpx;
				margin-bottom: 15rpx;
				color: #868686;
			}
			image{
				width: 25rpx;
				height: 20rpx;
				margin-left: 10rpx;
				transform: scaleY(-1);
			}
			
		}
		.zzc{
			 width: 100%;
			 height: 0%;
			 position: absolute;
			 background: rgba(0, 0, 0, 0.3);
			 z-index: 999;
			 transition: all 1s;
			 .zzc-list{
				 width: 90%;
				 margin: 0 auto;
				 display: flex;
				 justify-content: space-between;
				 color: #000;
				 font-size: 28rpx;
				 padding:25rpx 0;
				 background-color: #fff;
				 transition: all 1s;
			 }
		}
	}
</style>
