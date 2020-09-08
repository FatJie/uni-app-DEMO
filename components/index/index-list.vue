<template>
	<view class="index-list animated fadeInLeft fast">
		<view class="index-list1">
			<view>
				<image :src="item.userpic" mode="widthFix" lazy-load></image>{{item.username}}
			</view>
			<view v-show="!isguanzhu">
				<view class="icon iconfont icon-zengjia" @tap="guanzhu"></view>关注
			</view>
		</view>
		<view class="index-list2" @tap="opendetail">{{item.title}}</view>
		<view class="index-list3 u-f-ajc" @tap="opendetail">
			<!-- 图片 -->
			<image :src="item.titlepic" mode=""></image>
			<!-- 视频 -->
			<template v-if="item.type=='video'">
				<view class="icon iconfont icon-bofang index-list-play"></view>
				<view class="index-list-playinfo">{{item.playnum}}播放 {{item.long}}</view>
			</template>
			
		</view>
		<view class="index-list4">
			<view>
				<view :class="{'active':infonum.index==1}" @tap="caozuo('ding')"><view class="icon iconfont icon-icon_xiaolian-mian"></view>{{infonum.dingnum}}</view>
				<view :class="{'active':infonum.index==2}"><view class="icon iconfont icon-kulian" @tap="caozuo('cai')"></view>{{infonum.cainum}}</view>
			</view>
			<view>
				<view><view class="icon iconfont icon-pinglun1"></view>{{item.comment}}</view>
				<view><view class="icon iconfont icon-zhuanfa"></view>{{item.sharenum}}</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			item:Object,
			index:Number
		},
		data() {
			return {
				isguanzhu: this.item.isguanzhu,
				infonum:this.item.infonum
			}
		},
		methods:{
			guanzhu(){
				this.isguanzhu=true;
				uni.showToast({
					title: '关注成功！'
				});
			},
			//顶踩
			caozuo(type){
				switch (type){
					case 'ding':
						if(this.infonum.index==1){return;};
						this.infonum.dingnum++;
						if(this.infonum.index==2){
							this.infonum.cainum--;
						}
						this.infonum.index=1;
						break;
					case 'cai':
						if(this.infonum.index==2){return};
						this.infonum.cainum++;
						if(this.infonum.index==1){
							this.infonum.dingnum--;
						}
						this.infonum.index=2;
						break;
				}
			},
			//进入详情页
			opendetail(){
				uni.navigateTo({
					url:'../../pages/detail/detail?detailData='+JSON.stringify(this.item)
				})
			}
		}
	}
</script>

<style scoped>
	.index-list1>view:first-child,.index-list1>view:last-child,.index-list4>view:first-child,.index-list4>view:last-child,.index-list4>view>view{
		display: flex;
		align-items: center;
	}
	
	.index-list{
		padding: 20upx;
		border-bottom: 1upx solid #eee;
	}
	.index-list1{
		display: flex;
		justify-content: space-between;
		align-items: center;
	}
	.index-list1>view:first-child{
		color: #999;
	}
	.index-list1>view:last-child{
		background-color: #f4f4f4;
		border-radius: 5upx;
		padding: 0 10upx;
	}
	
	.index-list1>view:first-child image{
		width:90upx;
		height: 90upx;
		border-radius: 100%;
		margin-right: 10upx;
	}
	.index-list2{
		padding-top: 15upx;
		font-size: 32upx;
	}
	.index-list3{
		padding-top: 15upx;
		position: relative;
	}
	.index-list-play{
		position: absolute;
		font-size: 140upx;
		color: #fff;
	}
	.index-list-playinfo{
		position: absolute;
		background: rgba(51,51,51,0.72);
		color: #fff;
		bottom: 8upx;
		right: 8upx;
		border-radius: 40upx;
		font-size: 22upx;
		padding: 0 12upx;
	}
	.index-list3 image{
		width:100%;
		border-radius: 20upx;
	}
	.index-list4{
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 15upx 0;
	}
	.index-list4 view{
		color: #999;
	}
	.icon{
		margin-right: 10upx;
	}
	.index-list4>view>view:first-child{
		margin-right: 10upx; 
	}
	.index-list4 .active,.index-list4 .active>view{
		color: #c5f61c;
	}
</style>
