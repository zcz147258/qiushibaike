<template>
	<view>
		<view class="index-list animated bounceInLeft" v-for="(item,index) in items" :key="index">
			<view class="index-list1">
				<view>
					<image :src="item.userpic"
					 mode="widthFix"
					 lazy-load></image>
					 {{ item.username }}
				</view>
				<view v-show="item.isguanzhu" @tap="guanzhu(index)">
					<view class="iconfont icon icon-zengjia"></view>关注
				</view>
			</view>
			<view class="index-list2">{{ item.title }}</view>
			<view class="index-list3">
				<image :src="item.titlepic"
				 mode="widthFix"
				 lazy-load></image>
				 <!-- 视频 -->
				 <template v-if="item.type == 'video'">
				 	<view class="index-list-play icon iconfont icon-bofang"></view>
				 	<view class="index-list-playinfo">{{ item.playnum }} {{ item.long }}</view>
				 </template>
			</view>
			<view class="index-list4">
				<view>
					<view class="icon iconfont icon-icon_xiaolian-mian"
					:class="{'active':(item.infonum.index == 1)}"
					@tap="caozuo('ding')"></view><view>
					{{item.infonum.dingnum}}</view>
					<view class="icon iconfont icon-kulian"
					:class="{'active':(item.infonum.index == 2)}"
					@tap="caozuo('cai')"></view><view>
					{{item.infonum.cainum}}</view>
				</view>
				<view>
					<view class="icon iconfont icon-pinglun1"></view><view>
					{{item.commentnum}}</view>
					<view class="icon iconfont icon-zhuanfa"></view><view>
					{{item.sharenum}}</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data(){
			return {
				
			}
		},
		props: ['items'],
		methods:{
			guanzhu(index){
				this.$emit('guanzhu',index)
				// this.isguanzhu[index].isgaunzhu = false;
				// console.log(this.items[index].isguanzhu)
				uni.showToast({
					title:'关注成功',
				})
			}
		}
	}
</script>

<style scoped>
	.index-list{
		padding: 20upx;
		border-bottom: 1upx solid #EEEEEE;
	}
	.index-list1{
		display: flex;
		justify-content: space-between;
		align-items: center;
	}
	.index-list1>view:first-child{
		display: flex;
		align-items: center;
		color: #999999;
	}
	.index-list1>view:last-child{
		display: flex;
		align-items: center;
		background-color: #EEEEEE;
		border-radius: 10upx;
		padding: 0 10upx;
	}
	.index-list1>view:first-child image{
		width: 80upx;
		height: 80upx;
		border-radius: 100%;
		margin-right: 10upx;
	}
	.index-list2{
		padding: 15upx;
	}
	.index-list3{
		padding-top: 15upx;
		position: relative;
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.index-list3 image{
		width: 100%;
		border-radius: 20upx;
	}
	.index-list-play{
		position: absolute;
		font-size: 120upx;
		color: white;
	}
	.index-list-playinfo{
		position: absolute;
		color: #FFFFFF;
		background-color: rgba(51, 51, 51, 0.72);
		padding: 5upx 12upx;
		bottom: 16upx;
		right: 16upx;
		border-radius: 30upx;
	}
	.index-list4{
		display: flex;
		justify-content: space-between;
		align-items: center;
		color: #999999;
		margin-top: 15upx;
	}
	.index-list4>view:first-child{
		display: flex;
		align-items: center;
	}
	.index-list4>view:last-child{
		display: flex;
		align-items: center;
	}
	.index-list4>view>view>view{
		margin-right: 15upx;
	}
	.index-list4>view>view:nth-child(2n){
		margin-right: 15upx;
	}
	.index-list4>view>view:nth-child(2n-1){
		margin-right: 10upx;
	}
	.index-list4 .active{
		color: #c5f61c;
	}
</style>
