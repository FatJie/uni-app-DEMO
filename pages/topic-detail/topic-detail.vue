<template>
	<view>
		<!-- 话题介绍 -->
		<topic-info :item="topicInfo"></topic-info>
		<!-- tab切换 -->
		<swiper-tap-head :tabBars="tabBars" :tabIndex="tabIndex" @tabtap="tabtap" scrollItemStyle="width:50%;" scrollStyle="borber-bottom:0;"></swiper-tap-head>
		<!-- 列表 -->
		<view class="topic-detail-list">
			<block v-for="(item,index) in tablist" :key="index">
				<template v-if="tabIndex==index">
					<!-- 列表 -->
					<block v-for="(list,listindex) in item.list" :key="listindex">
						<common-list :item="list" :index="listindex"></common-list>
					</block>
					<!-- 上拉加载 -->
					<load-more :loadtext="item.loadtext"></load-more>
				</template>
			</block>
		</view>
	</view>
</template>

<script>
	import topicInfo from "../../components/topic/topic-info.vue";
	import swiperTapHead from "../../components/index/swiper-tap-head.vue";
	import commonList from "../../components/common/common-list.vue";
	import loadMore from "../../components/common/load-more.vue";
	export default {
		components:{
			topicInfo,
			swiperTapHead,
			commonList,
			loadMore
		},
		data() {
			return {
				tablist:[
					{
						loadtext:'上拉加载更多',
						list:[
							// 文字
							{
								userpic:'../../static/demo/userpic/12.jpg',
								username:'胖杰',
								sex:0,  // 0：男；1：女
								age:25,
								isguanzhu:false,
								title:'我是标题',
								titlepic:'',
								video:false,
								share:false,
								path:'深圳 龙岗',
								sharenum:20,
								commentnum:30,
								goodnum:40
							},
							// 图文
							{
								userpic:'../../static/demo/userpic/12.jpg',
								username:'胖杰',
								sex:0,  // 0：男；1：女
								age:25,
								isguanzhu:false,
								title:'我是标题',
								titlepic:'../../static/demo/datapic/13.jpg',
								video:false,
								share:false,
								path:'深圳 龙岗',
								sharenum:20,
								commentnum:30,
								goodnum:40
							},
							// 视频
							{
								userpic:'../../static/demo/userpic/12.jpg',
								username:'胖杰',
								sex:0,  // 0：男；1：女
								age:25,
								isguanzhu:false,
								title:'我是标题',
								titlepic:'../../static/demo/datapic/13.jpg',
								video:{
									looknum:'20w',
									long:'2:47'
								},
								share:false,
								path:'深圳 龙岗',
								sharenum:20,
								commentnum:30,
								goodnum:40
							},
							// 分享
							{
								userpic:'../../static/demo/userpic/12.jpg',
								username:'胖杰',
								sex:0,  // 0：男；1：女
								age:25,
								isguanzhu:false,
								title:'我是标题',
								titlepic:'',
								video:false,
								share:{
									title:'我是分享标题',
									titlepic:'../../static/demo/datapic/14.jpg'
								},
								path:'深圳 龙岗',
								sharenum:20,
								commentnum:30,
								goodnum:40
							}
						]
					},
					{
						loadtext:'上拉加载更多',
						list:[
							// 文字
							{
								userpic:'../../static/demo/userpic/12.jpg',
								username:'胖杰',
								sex:0,  // 0：男；1：女
								age:25,
								isguanzhu:false,
								title:'我是标题',
								titlepic:'',
								video:false,
								share:false,
								path:'深圳 龙岗',
								sharenum:20,
								commentnum:30,
								goodnum:40
							},
							// 图文
							{
								userpic:'../../static/demo/userpic/12.jpg',
								username:'胖杰',
								sex:0,  // 0：男；1：女
								age:25,
								isguanzhu:false,
								title:'我是标题',
								titlepic:'../../static/demo/datapic/13.jpg',
								video:false,
								share:false,
								path:'深圳 龙岗',
								sharenum:20,
								commentnum:30,
								goodnum:40
							},
							// 视频
							{
								userpic:'../../static/demo/userpic/12.jpg',
								username:'胖杰',
								sex:0,  // 0：男；1：女
								age:25,
								isguanzhu:false,
								title:'我是标题',
								titlepic:'../../static/demo/datapic/13.jpg',
								video:{
									looknum:'20w',
									long:'2:47'
								},
								share:false,
								path:'深圳 龙岗',
								sharenum:20,
								commentnum:30,
								goodnum:40
							},
							// 分享
							{
								userpic:'../../static/demo/userpic/12.jpg',
								username:'胖杰',
								sex:0,  // 0：男；1：女
								age:25,
								isguanzhu:false,
								title:'我是标题',
								titlepic:'',
								video:false,
								share:{
									title:'我是分享标题',
									titlepic:'../../static/demo/datapic/14.jpg'
								},
								path:'深圳 龙岗',
								sharenum:20,
								commentnum:30,
								goodnum:40
							}
						]
					},
				],
				tabBars:[
					{ name:"默认",id:"moren" },
					{ name:"最新",id:"zuixin" }
				],
				tabIndex:0,
				topicInfo:{
					titlepic:"../../static/demo/topicpic/13.jpeg",
					title:"忆往事，敬余生",
					desc:"我是描述",
					totalnum:"10000",
					todaynum:"10000"
				}
			}
		},
		// 上拉触底事件
		onReachBottom() {
			this.loadmore();
		},
		// 下拉刷新事件
		onPullDownRefresh() {
			this.getData();
		},
		methods: {
			// 下拉刷新事件
			getData(){
				setTimeout(()=>{
					// 获取数据
					var arr=[
								// 文字
								{
									userpic:'../../static/demo/userpic/12.jpg',
									username:'胖杰要瘦十斤一百斤一千斤',
									sex:0,  // 0：男；1：女
									age:25,
									isguanzhu:false,
									title:'我是标题1111111111111111111',
									titlepic:'',
									video:false,
									share:false,
									path:'深圳 龙岗',
									sharenum:20,
									commentnum:30,
									goodnum:40
								},
								// 图文
								{
									userpic:'../../static/demo/userpic/12.jpg',
									username:'胖杰',
									sex:0,  // 0：男；1：女
									age:25,
									isguanzhu:false,
									title:'我是标题',
									titlepic:'../../static/demo/datapic/13.jpg',
									video:false,
									share:false,
									path:'深圳 龙岗',
									sharenum:20,
									commentnum:30,
									goodnum:40
								},
								// 视频
								{
									userpic:'../../static/demo/userpic/12.jpg',
									username:'胖杰',
									sex:0,  // 0：男；1：女
									age:25,
									isguanzhu:false,
									title:'我是标题',
									titlepic:'../../static/demo/datapic/13.jpg',
									video:{
										looknum:'20w',
										long:'2:47'
									},
									share:false,
									path:'深圳 龙岗',
									sharenum:20,
									commentnum:30,
									goodnum:40
								},
								// 分享
								{
									userpic:'../../static/demo/userpic/12.jpg',
									username:'胖杰',
									sex:0,  // 0：男；1：女
									age:25,
									isguanzhu:false,
									title:'我是标题',
									titlepic:'',
									video:false,
									share:{
										title:'我是分享标题',
										titlepic:'../../static/demo/datapic/14.jpg'
									},
									path:'深圳 龙岗',
									sharenum:20,
									commentnum:30,
									goodnum:40
								}
							]
					// 赋值
					this.tablist.list=arr;
					// 关闭下拉刷新
					uni.stopPullDownRefresh();
				},2000)
			},
			// 上拉加载
			loadmore(){
				if(this.tablist[this.tabIndex].loadtext!="上拉加载更多"){return};
				this.tablist[this.tabIndex].loadtext="加载中...";
				setTimeout(()=>{
					let obj={
						userpic:'../../static/demo/userpic/12.jpg',
						username:'胖杰',
						sex:0,  // 0：男；1：女
						age:25,
						isguanzhu:false,
						title:'我是标题',
						titlepic:'../../static/demo/datapic/13.jpg',
						video:false,
						share:false,
						path:'深圳 龙岗',
						sharenum:20,
						commentnum:30,
						goodnum:40
					};
					this.tablist[this.tabIndex].list.push(obj);
					this.tablist[this.tabIndex].loadtext="上拉加载更多"
				},1000);
				// this.tablist[this.tabIndex].loadtext="没有更多数据了"
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
