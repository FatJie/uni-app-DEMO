<template>
	<view class="topic-nav">
		<view class="u-f-ac u-f-jsb">
			<view>热门分类</view>
			<view class="u-f-ac" @tap="openTapicNav">
				更多<view class="icon iconfont icon-jinru"></view>
			</view>
		</view>
		<view class="u-f-ac">
			<block v-for="(item,index) in nav" :key="index">
				<view>{{item.name}}</view>
			</block>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			nav:Array
		},
		methods:{
			openTapicNav(){
				uni.navigateTo({
					url:'../../pages/topic-nav/topic-nav'
				})
			}
		}
	}
</script>

<style scoped>
	/* 热门分类 */
	.topic-nav{
		border-bottom: 1upx solid #eee;
		border-top: 1upx solid #eee;
		padding: 20upx;
	}
	.topic-nav>view:first-child{
		margin-bottom: 10upx;
	}
	.topic-nav>view:first-child view{
		color: #9e9e9e;
	}
	.topic-nav>view:first-child>view:first-child{
		color: #333;
		font-size: 32upx;
	}
	.topic-nav>view:last-child>view{
		flex: 1;
		background: #f4f4f4;
		color: #9e9e9e;
		border-radius: 10upx;
		margin: 0 10upx;
		text-align: center;
	}
</style>
