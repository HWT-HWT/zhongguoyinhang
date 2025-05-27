<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	/* 处理iOS 100vh计算问题 */
	/* @supports (-webkit-touch-callout: none) {
	  .login {
	    min-height: -webkit-fill-available;
	  }
	} */
</style>
