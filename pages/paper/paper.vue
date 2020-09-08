<template>
	<view class="body">
		<!-- 操作菜单 -->
		<paper-left-popup :show="show" @hide="hidepopup" @addfrend="addfrend" @clear="clear"></paper-left-popup>
		<!-- 小纸条列表 -->
		<block v-for="(item,index) in list" :key="index">
			<paper-list :item="item" :index="index"></paper-list>
		</block>
		<!-- 上拉加载 -->
		<load-more :loadtext="loadtext"></load-more>
		
	</view>
</template>

<script>
	import uniBadge from "../../components/uni-badge/uni-badge.vue";
	import paperList from "../../components/paper/paper-list.vue";
	import loadMore from "../../components/common/load-more.vue";
	import paperLeftPopup from "../../components/paper/paper-left-popup.vue";
	export default {
		components:{
			paperList,
			loadMore,
			paperLeftPopup
		},
		data() {
			return {
				show:false,
				loadtext:"上拉加载更多",
				list:[
					{
						userpic:'../../static/demo/userpic/12.jpg',
						username:'昵称',
						time:'10:21',
						data:'我是信息',
						noreadnum:100
					},
					{
						userpic:'../../static/demo/userpic/12.jpg',
						username:'昵称',
						time:'10:21',
						data:'我是信息',
						noreadnum:0
					},
					{
						userpic:'../../static/demo/userpic/12.jpg',
						username:'昵称',
						time:'10:21',
						data:'我是信息',
						noreadnum:0
					},
					{
						userpic:'../../static/demo/userpic/12.jpg',
						username:'昵称',
						time:'10:21',
						data:'我是信息',
						noreadnum:15
					},
					{
						userpic:'../../static/demo/userpic/12.jpg',
						username:'昵称',
						time:'10:21',
						data:'我是信息',
						noreadnum:100
					},
					{
						userpic:'../../static/demo/userpic/12.jpg',
						username:'昵称',
						time:'10:21',
						data:'我是信息',
						noreadnum:0
					},
					{
						userpic:'../../static/demo/userpic/12.jpg',
						username:'昵称',
						time:'10:21',
						data:'我是信息',
						noreadnum:0
					},
					{
						userpic:'../../static/demo/userpic/12.jpg',
						username:'昵称',
						time:'10:21',
						data:'我是信息',
						noreadnum:15
					},
					{
						userpic:'../../static/demo/userpic/12.jpg',
						username:'昵称',
						time:'10:21',
						data:'我是信息',
						noreadnum:100
					},
					{
						userpic:'../../static/demo/userpic/12.jpg',
						username:'昵称',
						time:'10:21',
						data:'我是信息',
						noreadnum:0
					},
					{
						userpic:'../../static/demo/userpic/12.jpg',
						username:'昵称',
						time:'10:21',
						data:'我是信息',
						noreadnum:0
					},
					{
						userpic:'../../static/demo/userpic/12.jpg',
						username:'昵称',
						time:'10:21',
						data:'我是信息',
						noreadnum:15
					}
				]
			}
		},
		// 监听下拉刷新
		onPullDownRefresh() {
			this.getData();
		},
		// 监听页面上拉触底函数
		onReachBottom() {
			this.loadmore();
		},
		// 监听导航栏按钮点击事件
		onNavigationBarButtonTap(e) {
			switch (e.index){
				case 0:
				uni.navigateTo({
					url: '../user-list/user-list'
				});
				this.hidepopup();
					break;
				case 1:
				this.showpopup();
					break;
			}
		},
		methods: {
			// 操作菜单
			addfrend(){
				console.log("添加糗友");
				this.hidepopup();
			},
			clear(){
				console.log("清除缓存");
				this.hidepopup();
			},
			hidepopup(){
				this.show=false;
			},
			showpopup(){
				this.show=true;
			},
			// 上拉加载
			loadmore(){
				if(this.loadtext!="上拉加载更多"){return};
				this.loadtext="加载中...";
				setTimeout(()=>{
					let obj={
						userpic:'../../static/demo/userpic/12.jpg',
						username:'昵称',
						time:'10:21',
						data:'我是信息',
						noreadnum:15
					};
					this.list.push(obj);
					this.loadtext="上拉加载更多"
				},1000);
				// this.loadtext="没有更多数据了"
			},
			// 获取数据
			getData(){
				setTimeout(() => {
					// 获取数据
					let arr= [
						{
							userpic:'../../static/demo/userpic/12.jpg',
							username:'昵称123456',
							time:'10:21',
							data:'我是信息',
							noreadnum:185
						},
						{
							userpic:'../../static/demo/userpic/12.jpg',
							username:'昵称321654',
							time:'10:21',
							data:'我是信息',
							noreadnum:166
						},
						{
							userpic:'../../static/demo/userpic/12.jpg',
							username:'昵称',
							time:'10:21',
							data:'我是信息',
							noreadnum:2333
						},
						{
							userpic:'../../static/demo/userpic/12.jpg',
							username:'昵称',
							time:'10:21',
							data:'我是信息',
							noreadnum:666
						}
					]
					// 赋值
					this.list=arr;
					// 关闭下拉刷新
					uni.stopPullDownRefresh();
				}, 1000);
			}
		}
	}
</script>

<style>
	.body{
		padding: 0 20upx;
	}
	
</style>
