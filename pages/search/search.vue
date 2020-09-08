<template>
	<view>
		<template v-if="list.length>0">
			<block v-for="(item,index) in list" :key="index">
				<index-list :item="item" :index="index"></index-list>
			</block>
			<load-more :loadtext="loadtext"></load-more>
		</template>
		<template v-else-if="issearch && list.length<1">
			<nothing></nothing>
		</template>
	</view>
</template>

<script>
	import indexList from "../../components/index/index-list.vue";
	import nothing from "../../components/common/nothing.vue";
	import loadMore from "../../components/common/load-more.vue";
	export default {
		components:{
			indexList,
			nothing,
			loadMore
		},
		data() {
			return {
				issearch:false,
				loadtext:"上拉加载更多",
				list:[],
				searchtext:""
			}
		},
		// 监听点击取消按钮返回上一级页面
		onNavigationBarButtonTap(e) {
			if(e.index==0){
				uni.navigateBack({
					delta:1
				})
			}
		},
		// 监听搜索框文本变化
		onNavigationBarSearchInputChanged(e) {
			this.searchtext=e.text;
		},
		// 监听搜索框输入内容后回车
		onNavigationBarSearchInputConfirmed(e) {
			console.log(e.text);
			if(e.text){
				this.getdata();
			}
		},
		//监听页面触底事件
		onReachBottom(){
			this.loadmore();
		},
		// 监听下拉刷新
		onPullDownRefresh() {
			this.getdata();
			uni.stopPullDownRefresh();
		},
		methods: {
			// 搜索事件
			getdata(){
				
				uni.showLoading();
				// 请求服务器
				setTimeout(()=>{
					let arr=[
						{
							userpic:'../../static/demo/userpic/12.jpg',
							username:'胖杰',
							isguanzhu:false,
							title:'标题',
							type:'img',  //img:图文；video:视频
							titlepic:'../../static/demo/datapic/11.jpg',
							playnum:20000,
							long:'2:47',
							infonum:{
								index:1,  //0：没有操作；1：顶；2：踩；
								dingnum:11,
								cainum:11
							},
							comment:10,
							sharenum:10
						},
						{
							userpic:'../../static/demo/userpic/12.jpg',
							username:'胖杰',
							isguanzhu:true,
							title:'标题',
							type:'video',  //img:图文；video:视频
							titlepic:'../../static/demo/datapic/11.jpg',
							playnum:20000,
							long:'2:47',
							infonum:{
								index:2,  //0：没有操作；1：顶；2：踩；
								dingnum:11,
								cainum:11
							},
							comment:10,
							sharenum:10
						}
					];
					this.list=arr;
					uni.hideLoading();
					this.issearch=true;
				},1000);
			},
			// 上拉加载
			loadmore(index){
				if(this.loadtext!="上拉加载更多"){return};
				this.loadtext="加载中...";
				setTimeout(()=>{
					let obj={
						userpic:'../../static/demo/userpic/12.jpg',
						username:'胖杰',
						isguanzhu:false,
						title:'标题',
						type:'img',  //img:图文；video:视频
						titlepic:'../../static/demo/datapic/11.jpg',
						playnum:20000,
						long:'2:47',
						infonum:{
							index:1,  //0：没有操作；1：顶；2：踩；
							dingnum:11,
							cainum:11
						},
						comment:10,
						sharenum:10
					};
					this.list.push(obj);
					this.loadtext="上拉加载更多"
				},1000);
				// this.loadtext="没有更多数据了";
			},
		}
	}
</script>

<style>

</style>
