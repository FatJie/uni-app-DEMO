<template>
	<view class="body">
		<!-- tab切换 -->
		<swiper-tap-head :tabBars="tabBars" :tabIndex="tabIndex" @tabtap="tabtap" scrollItemStyle="width:33%;" scrollStyle="borber-bottom:0;"></swiper-tap-head>
		
		<!-- 好友列表 -->
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:swiperheight+'px'}" :current="tabIndex" @change="tabChange">
				<swiper-item v-for="(items,index) in newsList" :key="index">
					<scroll-view class="list" scroll-y @scrolltolower="loadmore(index)">
						<template v-if="items.list.length>0">
							<!-- 图文列表 -->
							<block v-for="(item,index1) in items.list" :key="index1">
								<user-list :item="item" :index="index1"></user-list>
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
	</view>
</template>

<script>
	import swiperTapHead from "../../components/index/swiper-tap-head.vue";
	import userList from "../../components/user-list/user-list.vue";
	import loadMore from "../../components/common/load-more.vue";
	import nothing from "../../components/common/nothing.vue";
	export default {
		components:{
			swiperTapHead,
			userList,
			loadMore,
			nothing
		},
		data() {
			return {
				newsList:[
					{
						loadtext:"上拉加载更多",
						list:[
							{
								userpic:'../../static/demo/userpic/11.jpg',
								username:'胖杰',
								age:20,
								sex:0,
								isguanzhu:true
							},
							{
								userpic:'../../static/demo/userpic/11.jpg',
								username:'妞妞',
								age:18,
								sex:1,
								isguanzhu:false
							},
							{
								userpic:'../../static/demo/userpic/11.jpg',
								username:'胖杰',
								age:20,
								sex:0,
								isguanzhu:true
							},
							{
								userpic:'../../static/demo/userpic/11.jpg',
								username:'妞妞',
								age:18,
								sex:1,
								isguanzhu:false
							},
							{
								userpic:'../../static/demo/userpic/11.jpg',
								username:'胖杰',
								age:20,
								sex:0,
								isguanzhu:true
							},
							{
								userpic:'../../static/demo/userpic/11.jpg',
								username:'妞妞',
								age:18,
								sex:1,
								isguanzhu:false
							},
							{
								userpic:'../../static/demo/userpic/11.jpg',
								username:'胖杰',
								age:20,
								sex:0,
								isguanzhu:true
							},
							{
								userpic:'../../static/demo/userpic/11.jpg',
								username:'妞妞',
								age:18,
								sex:1,
								isguanzhu:false
							},
							{
								userpic:'../../static/demo/userpic/11.jpg',
								username:'胖杰',
								age:20,
								sex:0,
								isguanzhu:true
							},
							{
								userpic:'../../static/demo/userpic/11.jpg',
								username:'妞妞',
								age:18,
								sex:1,
								isguanzhu:false
							}
						]
					},
					{
						loadtext:"上拉加载更多",
						list:[
							{
								userpic:'../../static/demo/userpic/11.jpg',
								username:'胖杰222',
								age:20,
								sex:0,
								isguanzhu:true
							},
							{
								userpic:'../../static/demo/userpic/11.jpg',
								username:'妞妞',
								age:18,
								sex:1,
								isguanzhu:false
							}
						]
					},
					{
						loadtext:"上拉加载更多",
						list:[
							{
								userpic:'../../static/demo/userpic/11.jpg',
								username:'胖杰333',
								age:20,
								sex:0,
								isguanzhu:true
							},
							{
								userpic:'../../static/demo/userpic/11.jpg',
								username:'妞妞',
								age:18,
								sex:1,
								isguanzhu:false
							}
						]
					}
				],
				swiperheight:'',
				tabBars:[
					{ name:"互关",id:"huguan",num:40 },
					{ name:"关注",id:"guanzhu",num:20 },
					{ name:"粉丝",id:"fans",num:66 }
				],
				tabIndex:0,
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
		// 监听导航按钮事件
		onNavigationBarButtonTap(e) {
			if(e.index==0){
				uni.navigateBack({
					delta: 1
				});
			}
		},
		methods: {
			// 上拉加载
			loadmore(index){
				if(this.newsList[index].loadtext!="上拉加载更多"){return};
				this.newsList[index].loadtext="加载中...";
				setTimeout(()=>{
					let obj={
						userpic:'../../static/demo/userpic/11.jpg',
						username:'胖杰666',
						age:20,
						sex:0,
						isguanzhu:true
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
