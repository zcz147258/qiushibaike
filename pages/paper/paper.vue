<template>
	<view>
		测试一下消息推送{{name}}
	</view>
</template>

<script>
	export default {
		data() {
			return {
				name: '111'
			}
		},
		onShow() {
			//监听系统通知栏消息点击事件
			plus.push.addEventListener('click', function(msg){  
			    //处理点击消息的业务逻辑代码  
			}, false);  
			//监听接收透传消息事件 
			var _this = this
			plus.push.addEventListener('receive', function(msg){
			    //处理透传消息的业务逻辑代码  
				_this.name = JSON.parse((JSON.stringify(msg.content)))
				console.log(JSON.parse((JSON.stringify(msg.content))));
				uni.showToast({
					title: ''+ JSON.stringify(msg)
				})
			}, false);
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
