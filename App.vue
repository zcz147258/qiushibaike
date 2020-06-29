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
	@import './common/iconfont.css';
	/* 引入样式阿里巴巴 */
	@import './common/uni.css';
	/* 引入公共样式库 */
	@import './common/common.css';
	@import './common/animate.min.css';
	/* 引入动画库 */
</style>
