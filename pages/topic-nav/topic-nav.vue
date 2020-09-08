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
							<!-- 话题列表 -->
							<view class="topic-view">
								<block v-for="(item,index1) in items.list" :key="index1">
									<topic-list :item="item" :index="index1"></topic-list>
								</block>
							</view>
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
		
	</view>
</template>

<script>
	import swiperTapHead from "../../components/index/swiper-tap-head.vue";
	import nothing from "../../components/common/nothing.vue";
	import loadMore from "../../components/common/load-more.vue";
	import topicList from "../../components/news/topic-list.vue";
	export default {
		components:{
			swiperTapHead,
			nothing,
			loadMore,
			topicList
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
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
								},
								{
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
								},
								{
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
								},
								{
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
								},
								{
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
								},
								{
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
								},
								{
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
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
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
								},
								{
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
								},
								{
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
								},
								{
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
								},
								{
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
								},
								{
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
								},
								{
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
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
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
								},
								{
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
								},
								{
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
								},
								{
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
								},
								{
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
								},
								{
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
								},
								{
									titlepic:'../../static/demo/topicpic/13.jpeg',
									title:'话题名称',
									desc:'描述',
									totalnum:50,
									todaynum:10
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
		methods: {
			// 上拉加载
			loadmore(index){
				if(this.newsList[index].loadtext!="上拉加载更多"){return};
				this.newsList[index].loadtext="加载中...";
				setTimeout(()=>{
					let obj={
						titlepic:'../../static/demo/topicpic/13.jpeg',
						title:'话题名称',
						desc:'描述',
						totalnum:50,
						todaynum:10
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
	.topic-view{
		padding:0 20upx;
	}
</style>
