<template>
	<view>
	
		<!-- 顶部导航条 -->
		<swiper-tap-head :tabBars="tabBars" :tabIndex="tabIndex" @tabtap="tabtap"></swiper-tap-head>
		
		<!-- 内容面板滑动 -->
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:swiperheight+'px'}" :current="tabIndex" @change="tabChange">
				<swiper-item v-for="(items,index) in newsList" :key="index">
					<scroll-view class="list" scroll-y @scrolltolower="loadmore(index)">
						<template v-if="items.list.length>0">
							<!-- 图文列表 -->
							<block v-for="(item,index1) in items.list" :key="index1">
								<index-list :index="index" :item="item"></index-list>
							</block>
							<!-- 上拉加载 -->
							<load-more :loadtext="items.loadtext"></load-more>
						</template>
						<template v-else>
							<!-- 无内容默认 -->
							<nothing></nothing>
						</template>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
		
		<!--  -->
	</view>
</template>

<script>
	import indexList from "../../components/index/index-list.vue";
	import swiperTapHead from "../../components/index/swiper-tap-head.vue";
	import loadMore from "../../components/common/load-more.vue";
	import nothing from "../../components/common/nothing.vue";
	export default {
		components:{
			indexList,
			loadMore,
			swiperTapHead,
			nothing
		},
		data() {
			return {
				swiperheight:'',
				tabIndex:0,
				tabBars:[
					{name:"关注",id:"1"},
					{name:"推荐",id:"2"},
					{name:"热点",id:"3"},
					{name:"财经",id:"4"},
					{name:"娱乐",id:"5"},
					{name:"体育",id:"6"}
				],
				newsList:[
					{
						loadtext:"上拉加载更多",
						list:[
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
						]
					},
					{
						loadtext:"上拉加载更多",
						list:[
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
							},
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
						]
					},
					{
						loadtext:"上拉加载更多",
						list:[]
					},
					{
						loadtext:"上拉加载更多",
						list:[
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
						]
					},
					{
						loadtext:"上拉加载更多",
						list:[
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
						]
					},
					{
						loadtext:"上拉加载更多",
						list:[]
					},
				]
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					let height=res.windowHeight - uni.upx2px(100)
					this.swiperheight=height;
				}
			});
		},
		// 监听原生标题导航按钮点击事件(发布按钮)
		onNavigationBarButtonTap(e){
			switch (e.index){
				case 1:
					uni.navigateTo({
						url:'../add-input/add-input'
					});
					break;
			}
		},
		// 监听搜索框点击事件
		onNavigationBarSearchInputClicked(){
			uni.navigateTo({
				url:'../search/search'
			})
		},
		methods: {
			// 上拉加载
			loadmore(index){
				if(this.newsList[index].loadtext!="上拉加载更多"){return};
				this.newsList[index].loadtext="加载中...";
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
					this.newsList[index].list.push(obj);
					this.newsList[index].loadtext="上拉加载更多"
				},1000);
				
			},
			//点击事件
			tabtap(index){
				this.tabIndex=index;
			},
			//滑动事件
			tabChange(e){
				this.tabIndex=e.detail.current;
			}
		}
	}
</script>

<style>
	
</style>
