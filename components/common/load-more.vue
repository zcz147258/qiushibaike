<template>
	<view>
		<view class="load-more">{{ items.loadtext }}</view>
	</view>
</template>

<script>
	export default {
		props:['items'],
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style scoped>
.load-more{
	text-align: center;
	padding: 15upx;
	color: #BBBBBB;
}
</style>
