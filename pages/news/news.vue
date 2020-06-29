<template>
	<view>
		<!-- 自定义导航 -->
		<uni-nav-bar
		:statusBar="true" 
		@clickRight="openadd">
		<!-- 左边 -->
			<block slot="left">
				<view class="lefticon">
					<view class="icon iconfont icon-qiandao"></view>
				</view>
			</block>
		<!-- 中间 -->
			<view class="nav-tab-bar">
				<block v-for="(tab,index) in tarBars" :key="tab.id">
					<view :class="{'actived':tabIndex == index}" @tap="changetap(index)">
						<view>{{ tab.name }}
							<view v-if="(tabIndex == index)" class="nav-tab-bar-line"></view>
						</view>
					</view>
				</block>
				
			</view>
		<!-- 右边 -->
			<block slot="right">
				<view class="righticon">
					<view class="icon iconfont icon-bianji1"></view>
				</view>
			</block>
		</uni-nav-bar>
		
		<!-- 公共组件列表 -->
		<view class="common-list">
			<view class="common-list-l">
					<image src="../../static/demo/datapic/19.jpg" 
					lazy-load></image>
			</view>
				<view class="common-list-r">
					<view class="u-f-ac u-f-jsb">
						<view class="u-f-ac">
							<view>昵称</view>
							<view>18</view>
						</view>
						<view
						class="icon iconfont icon-zengjia">关注</view>
					</view>
					<view >标题</view>
					<view class="u-f-ajc">
						<template>
							
							<image src="../../static/demo/datapic/13.jpg" 
							mode="widthFix" 
							lazy-load></image>
						</template>
						
						<template>
							<view class="common-list-play icon iconfont icon-bofang">
							</view>
							<view class="common-list-playinfo">
								20w 次播放 1:45
							</view>
						</template>
						
						<!-- <view class="common-list-share u-f-ac">
							<image :src="item.share.titlepic" 
							mode="widthFix" lazy-load></image>
							<view>{{item.share.title}}</view>
						</view> -->
					</view>
					<view class="u-f-ac u-f-jsb">
						<view>深圳 龙岗</view>
						<view class="u-f-ac">
							<view class="icon iconfont icon-zhuanfa">
							10</view>
							<view class="icon iconfont icon-pinglun1">
							10</view>
							<view class="icon iconfont icon-dianzan1" @tap="caozuo('ding')">
							10</view>
						</view>
					</view>
				</view>
		</view>
	</view>
</template>

<script>
	import uniNavBar from '../../components/uni-nav-bar/uni-nav-bar.vue'
	export default {
		data() {
			return {
				tabIndex: 0,
				tarBars: [
					{
						name: '关注',
						id: 'guanzhu'
					},
					{
						name: '话题',
						id: 'hauti'
					}
				]
			}
		},
		components:{
			uniNavBar,
		},
		methods: {
			changetap(index){
				this.tabIndex = index
			},
			openadd(){
				uni.navigateTo({
					url: '../add-input/add-input'
				})
			}
		}
	}
</script>

<style scoped>
@import "../../common/list.css";
.lefticon view,.righticon view{
	font-size: 40upx;
}
.lefticon>view{
	margin-left: 25upx;
	color: #ff9619;
}
.nav-tab-bar{
	display: flex;
	justify-content: center;
	margin-left: 28%;
}
.nav-tab-bar>view{
	padding: 0 15upx;
	font-weight: bold;
	color: #969696;
	position: relative;
}
.nav-tab-bar>view>view{
		font-size: 32upx;
}
.actived>view{
	color: #333333;
}
.nav-tab-bar-line{
	border-bottom: 5upx solid #fede33;
	border-top: 5upx solid #fede33;
	width: 70upx;
	border-radius: 20upx;
	position: absolute;
	bottom: -3upx;
}
</style>
