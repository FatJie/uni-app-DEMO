<template>
	<view>
		<!-- 自定义导航栏 -->
		<uni-nav-bar :statusBar="true" rightText="发布" left-icon="arrowleft"  @clickLeft="back" @clickRight="submit">
			<view @tap="changelook"  class="uni-nav-bar-middle u-f-ajc">{{yinsi}}<view class="icon iconfont icon-xialazhankai"></view></view>
		</uni-nav-bar>
		<!-- 多行输入框 -->
		<view class="uni-textarea">
			<textarea v-model="text" placeholder="说一句话吧~" />
		</view>
		<!-- 上传多图功能 -->
		<upload-image @upload="upload"></upload-image>
		<!-- 弹出公告 -->
		<uni-popup :show="showpopup" position="middle" mode="fixed" @hidePopup="hidePopup">
			<view class="gonggao">
				<view class="u-f-ajc">
					<image src="../../static/common/addinput.png" mode="widthFix"></image>
				</view>
				<view>1.涉及黄色，政治，广告及骚扰信息</view>
				<view>2.涉及人身攻击</view>
				<view>3.留联系方式，透露他人隐私</view>
				<view>一经核实将被封禁，情节严重者将永久封禁</view>
				<button type="default" @tap="hidePopup">朕知道了</button>
			</view>
		</uni-popup>
	</view>
</template>

<script>
	
	let changelook=['所有人可见','仅自己可见']
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue";
	import uploadImage from "../../components/common/upload-image.vue";
	import uniPopup from "../../components/uni-popup/uni-popup.vue";
	export default {
		components:{
			uniNavBar,
			uploadImage,
			uniPopup
		},
		data() {
			return {
				isget:false,
				showpopup:true,
				yinsi:"所有人可见",
				text:'',
				imglist:[]
			}
		},
		// 监听返回事件
		onBackPress() {
			// 如果用户输入了信息
			if(!this.text && this.imglist.length<1){ return };
			if(!this.isget){
				this.baocun();
				return true;  //阻止返回默认行为
			}
		},
		methods: {
			// 保存为草稿
			baocun(){
				uni.showModal({
					content: '是否保存为草稿',
					cancelText: '不保存',
					confirmText: '保存',
					success: res => {
						if(res.confirm){
							
						}else{
							
						};
						this.isget=true;
						uni.navigateBack({
							delta:1
						})
					}
				});
			},
			upload(arr){
				this.imglist=arr;
			},
			// 返回
			back(){
				uni.navigateBack({
					delta:1
				})
			},
			// 发布
			submit(){
				console.log("发布")
			},
			// 隐私
			changelook(){
				uni.showActionSheet({
					itemList:changelook,  //按钮上的文字数组
					success:(res)=> {
						this.yinsi=changelook[res.tapIndex];
					}
				})
			},
			hidePopup(){
				this.showpopup=false;
			}
		}
	}
</script>

<style>
	.uni-textarea{
		border: 1upx solid #eee;
	}
	.gonggao{
		width:500upx;
	}
	.gonggao image{
		width:85%;
		margin-bottom: 20upx;
	}
	.gonggao button{
		background-color: #ffe934;
		color: #171606;
		margin-top: 20upx;
	}
	.uni-nav-bar-middle{
		width:100%;
	}
</style>
