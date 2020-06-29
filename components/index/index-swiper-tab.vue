<template>
	<view>
		<view class="uni-tab-bar">
			<scroll-view scroll-x="true"
			 class="uni-swiper-tab"
			 :scroll-left="scrollwidth"
			 scroll-with-animation="true">
				<block v-for="(tab,index) in tarBars" :key="tab.id">
					<view class="swiper-tab-list"
					 :class="{ 'active': tabIndex == index}"
					 @tap="tabtap(index)">
						{{ tab.name }}
						<view class="swiper-tab-line"></view>
					</view>
				</block>
			</scroll-view>
		</view>
	</view>
</template>

<script>
	export default {
		data(){
			return{
				scrollwidth: 0
			}
		},
		props:['tabIndex','tarBars'],
		methods:{
			tabtap(index){
				this.$emit('tabtap',index)
			}
		},
		watch:{
			tabIndex(){
				if(this.tabIndex>=3){
					this.scrollwidth = 80
				}
				if(this.tabIndex<3){
					this.scrollwidth = 0
				}
			}
		}
	}
</script>

<style>
	.swiper-tab-list{
		color: #969696;
		font-weight: bold;
	}
	.uni-tab-bar .active{
		color: #343434;
	}
	.active .swiper-tab-line{
		border-bottom: 6upx solid #fede33;
		width: 70upx;
		margin: auto;
		border-top: 6upx solid #FEDE33;
		border-radius: 20upx;
	}
</style>
