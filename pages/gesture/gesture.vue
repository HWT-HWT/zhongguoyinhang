<template>
	<view class="login">
		<view class="login-back">
			<occupyVue hight="90rpx"></occupyVue>
			<image class="left" src="@/static/upsdk_payment_right.webp" mode="" @click="Back"></image>
			<image src="@/static/boc_folder_title_service.png" mode=""></image>
		</view>
		<view class="login-logo">
			<image src="@/static/boc_login_logo_inte.png" mode=""></image>
		</view>
		<view class="login-Phone">
			132****8145
		</view>
		 <gesturePassword @change="gestureChange" ref="childRef" ></gesturePassword>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue';
	import gesturePassword from '@/components/gzz-gesture/gesture-password.vue';
	export default {
		data() {
			return {
				date:''
			};
		},
		components:{
			gesturePassword,
			occupyVue
		},
		methods:{
			refreshPage() {
			      uni.reload(); // 刷新当前页面
			},
			gestureChange(points){
				 const arr = [1,2,3,6,9]
				
				 function arraysAreEqual(arr1, arr2) {
					 // 首先检查两个数组的长度是否相等
					 if (arr1.length !== arr2.length) {
						
						 uni.showToast({
						 	title:'密码错误',
							icon:'none'
						 })
						 setTimeout(()=>{
							 uni.reLaunch({
							 	url:'/pages/index/index'
							 })
						 },400)
						 
						 return false;
					 }
				  
					 // 遍历数组，检查每个位置的元素是否相等
					 for (let i = 0; i < arr1.length; i++) {
						 if (arr1[i] !== arr2[i]) {
							 uni.showToast({
								title:'密码错误',
								icon:'none'
							 })
							setTimeout(()=>{
								 uni.reLaunch({
									url:'/pages/index/index'
								 })
							},400)
							 
							 return false;
						 }
					 }
					 // 如果所有元素都相等，则返回真
					 return true;
				 }

				if(arraysAreEqual(arr,points)){
					
					// 创建一个新的 Date 对象
					const now = new Date();
					 
					// 提取年、月、日、时、分、秒
					const year = now.getFullYear();
					const month = String(now.getMonth() + 1).padStart(2, '0'); // 月份从0开始，所以需要+1，并且确保是两位数
					const day = String(now.getDate()).padStart(2, '0'); // 确保是两位数
					const hours = String(now.getHours()).padStart(2, '0'); // 确保是两位数
					const minutes = String(now.getMinutes()).padStart(2, '0'); // 确保是两位数
					const seconds = String(now.getSeconds()).padStart(2, '0'); // 确保是两位数
					
					this.date =  `${year}-${month}-${day} ${hours}:${minutes}:${seconds}`
					
					
					uni.setStorageSync('OldDate',uni.getStorageSync('date'))
					
					uni.setStorageSync('date',this.date)
					
					
					uni.setStorageSync('account',{token:true})
					uni.showToast({
						title:'登录成功',
						icon:'none'
					})
					setTimeout(()=>{
						 uni.reLaunch({
							url:'/pages/index/index'
						 })
					},400)
				}
				
				
			},
			Back(){
				uni.reLaunch({
					url:'/pages/index/index'
				})
			},
			
		}
	}
</script>

<style lang="scss" scoped>
	.login{
		width: 100vw;
		height: 100vh;
		.login-back{
			display: flex;
			flex-wrap: wrap;
			align-items: center;
			justify-content: space-between;
			padding: 30rpx;
			.left{
				transform: scale(-1);
				width: 60rpx;
				height: 60rpx;
			}
			image{
				width: 40rpx;
				height: 40rpx;
				padding:0 10rpx;
				padding-top:10rpx;
			}
		}
		.login-logo{
			display: flex;
			align-items: center;
			justify-content: center;
			image{
				width: 200rpx;
				height: 200rpx;
			}
		}
		.login-Phone{
			display: flex;
			justify-content: center;
			margin: 50rpx 0;
			font-size: 45rpx;
		}
	}
</style>
