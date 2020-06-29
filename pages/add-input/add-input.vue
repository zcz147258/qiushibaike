<template>
	<view>
		<!-- 自定义导航栏 -->
		<uni-nav-bar 
		:statusBar="true" 
		rightText="发布" 
		left-icon="arrowleft" 
		@clickLeft="back"
		@clickRight="submit"
		>
		<view class="xila" @tap="changelook">
			{{yinsi}}
			<view class="icon iconfont icon-xialazhankai"></view>
			</view>
		</uni-nav-bar>
		<!-- 多行输入框 -->
		<view class="uni-textarea">
			<textarea value="" placeholder="说一句话吧~~" v-model="text"/>
		</view>
		<upload-image @upload="upload"></upload-image>
	</view>
</template>

<script>
	import uniNavBar from '../../components/uni-nav-bar/uni-nav-bar.vue';
	import uploadImage from '../../components/upload-image/upload-image.vue'
	let arr = ['所有人可见','仅自己可见'];
	export default {
		data() {
			return {
				yinsi: '所有人可见',
				text: '',
				imgList: []
			}
		},
		components:{
			uniNavBar,
			uploadImage
		},
		/* 监听页面返回 */
		onBackPress(){
			if(!this.text && this.imgList.length<1){
				return;
			}
			uni.showModal({
				title: '提示',
				content: '是否保存为草稿',
				cancelText: '不保存',
				confirmText: '保存',
				success: res => {
					if(res.confirm){
						
					}else{
						
					}
					uni.navigateBack({
						delta: 1
					})
				},
			});
		},
		methods: {
			back(){
				uni.navigateBack({
					delta: 1
				})
			},
			//发布事件
			submit(){
				console.log("发布")
			},
			//隐私
			changelook(){
				//调用官方接口
				uni.showActionSheet({
					itemList: arr,
					success:(res)=>{
							this.yinsi = arr[res.tapIndex]
					}
				});
			},
			upload(arr){
				this.imgList = arr
			}
		}
	}
</script>

<style scoped>
.xila{
	display: flex;
	justify-content: center;
	margin-left: 30%;
}
.uni-textarea{
	border: 1upx solid #EEEEEE;
	height: 400upx;
}
</style>
