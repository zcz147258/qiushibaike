<template>
	<view>
			<index-swiper-tab 
		:tabIndex="tabIndex" 
		:tarBars="tarBars"
		@tabtap="tabtap">
		</index-swiper-tab>
		
		
		<view class="uni-tab-bar">
			<swiper class="swiper-box"
			 :style="{height: swiperheight+'px'}"
			 :current="tabIndex"
			 @change="tabChange">
				<swiper-item v-for="(items,index) in newslist" :key="index">
					<scroll-view scroll-y="true" 
					class="list"
					@scrolltolower="loadmore(index)">
						<!-- 图文列表 -->
						<view>
							<index-list :items="items.list" @guanzhu="guanzhu"></index-list>
						</view>
						<!-- 上拉加载更多 -->
						<load-more :items="items"></load-more>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	import IndexList from '../../components/index/index-list.vue';
	import IndexSwiperTab from '../../components/index/index-swiper-tab.vue';
	import LoadMore from '../../components/common/load-more.vue'
	export default {
		data() {
			return {
				swiperheight: 500,
				newslist: [
					{
						loadtext: '上拉加载更多',
						list: [
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题",
								type: "img", /* 图文视频*/
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									dingnum: 11,
									cainum: 11,
									index: 1 /* 0没有操作 1：顶  2：踩*/
								},
								commentnum: 10,
								sharenum: 10
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题1",
								type: "img", /* 图文视频*/
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									dingnum: 11,
									cainum: 11,
									index: 1 /* 0没有操作 1：顶  2：踩*/
								},
								commentnum: 10,
								sharenum: 10
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", /* 图文视频*/
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									dingnum: 11,
									cainum: 11,
									index: 2 /* 0没有操作 1：顶  2：踩*/
								},
								commentnum: 10,
								sharenum: 10
							}
						]
					},
					{
						loadtext: '上拉加载更多',
						list: [
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题1",
								type: "img", /* 图文视频*/
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									dingnum: 11,
									cainum: 11,
									index: 1 /* 0没有操作 1：顶  2：踩*/
								},
								commentnum: 10,
								sharenum: 10
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题1",
								type: "img", /* 图文视频*/
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									dingnum: 11,
									cainum: 11,
									index: 1 /* 0没有操作 1：顶  2：踩*/
								},
								commentnum: 10,
								sharenum: 10
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", /* 图文视频*/
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									dingnum: 11,
									cainum: 11,
									index: 2 /* 0没有操作 1：顶  2：踩*/
								},
								commentnum: 10,
								sharenum: 10
							}
						]
					},
					{
						loadtext: '上拉加载更多',
						list: [
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题2",
								type: "img", /* 图文视频*/
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									dingnum: 11,
									cainum: 11,
									index: 1 /* 0没有操作 1：顶  2：踩*/
								},
								commentnum: 10,
								sharenum: 10
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", /* 图文视频*/
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									dingnum: 11,
									cainum: 11,
									index: 2 /* 0没有操作 1：顶  2：踩*/
								},
								commentnum: 10,
								sharenum: 10
							}
						]
					},
					{
						loadtext: '上拉加载更多',
						list: [
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题3",
								type: "img", /* 图文视频*/
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									dingnum: 11,
									cainum: 11,
									index: 1 /* 0没有操作 1：顶  2：踩*/
								},
								commentnum: 10,
								sharenum: 10
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", /* 图文视频*/
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									dingnum: 11,
									cainum: 11,
									index: 2 /* 0没有操作 1：顶  2：踩*/
								},
								commentnum: 10,
								sharenum: 10
							}
						]
					},
					{
						loadtext: '上拉加载更多',
						list: [
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题4",
								type: "img", /* 图文视频*/
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									dingnum: 11,
									cainum: 11,
									index: 1 /* 0没有操作 1：顶  2：踩*/
								},
								commentnum: 10,
								sharenum: 10
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", /* 图文视频*/
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									dingnum: 11,
									cainum: 11,
									index: 2 /* 0没有操作 1：顶  2：踩*/
								},
								commentnum: 10,
								sharenum: 10
							}
						]
					},
					{
						loadtext: '上拉加载更多',
						list: [
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题5",
								type: "img", /* 图文视频*/
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									dingnum: 11,
									cainum: 11,
									index: 1 /* 0没有操作 1：顶  2：踩*/
								},
								commentnum: 10,
								sharenum: 10
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", /* 图文视频*/
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									dingnum: 11,
									cainum: 11,
									index: 2 /* 0没有操作 1：顶  2：踩*/
								},
								commentnum: 10,
								sharenum: 10
							}
						]
					}
				],
				tabIndex: 0,
				tarBars: [
					{
						name: "关注",
						id: "guanzhu",
					},
					{
						name: "推荐",
						id: "tuijian",
					},
					{
						name: "体育",
						id: "tiyu",
					},
					{
						name: "热点",
						id: "redian",
					},
					{
						name: "财经",
						id: "caijing",
					},
					{
						name: "娱乐",
						id: "yule"
					}
				],
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) =>{
					let height = res.windowHeight - uni.upx2px(200);
					this.swiperheight = height
				}
			})
		},
		/* 监听默认搜索框 */
		onNavigationBarSearchInputClicked() {
			uni.navigateTo({
				url: '../search/search'
			})
		},
		onNavigationBarButtonTap(e){
			//进入跳转编辑发布
			switch(e.index){
				case 1:
				 uni.navigateTo({
				 	url: '../add-input/add-input',
				 });
					break;  
			}
		},
		methods: {
			//滑动事件 
			tabChange(e){
				this.tabIndex = e.detail.current
			},
			//tarbar 事件
			tabtap(index){
				this.tabIndex = index;
			},
			//父子组件修改数值
			guanzhu(index){
				this.newslist[this.tabIndex].list[index].isguanzhu = false;
			},
			//上拉加载更多
			loadmore(index){
				/* 避免一直加载 */
				if(this.newslist[index].loadtext!="上拉加载更多"){
					return;
				}
				let obj = {
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", /* 图文视频*/
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									dingnum: 11,
									cainum: 11,
									index: 2 /* 0没有操作 1：顶  2：踩*/
								},
								commentnum: 10,
								sharenum: 10
				};
				/* 改变状态 */
				this.newslist[index].loadtext = "加载中...";
				/* 控制加载的时间 */
				setTimeout(()=>{
					this.newslist[index].list.push(obj)
					this.newslist[index].loadtext = "上拉加载更多";
				},1000)
				// this.newslist[index].loadtext = "没有更多数据";
			}
		},
		components:{
			IndexList,
			IndexSwiperTab,
			LoadMore
		}
	}
</script>

<style>

</style>
