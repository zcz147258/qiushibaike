<template>
	<view>
		<!-- 自定义导航栏 -->
	</view>
</template>

<script>
	export default {
		data(){
			return {
				
			}
		},
		onNavigationBarButtonTap(e){
			if(e.index == 0){
				uni.navigateBack({
					delta: 1
				});
			}
		},
		//用户输入发生改变时
		onNavigationBarSearchInputChanged(e){
			console.log(e.text)
		},
		//监听搜索按钮
		onNavigationBarSearchInputConfirmed(e){
			console.log(e.text)
		},
		methods:{
			
		}
	}
</script>

<style>
</style>
