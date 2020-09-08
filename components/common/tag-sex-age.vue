<template>
	<view class="tag-sex icon iconfont" :class="[sex==0?'icon-nan':'icon-nv']">{{age}}</view>
</template>

<script>
	export default{
		props:{
			sex:Number,
			age:Number
		}
	}
</script>

<style scoped>
	.tag-sex{
		padding: 5upx 10upx;
		color: #fff;
		background-color: #007AFF;
		border-radius: 20upx;
		margin-left: 10upx;
		font-size: 23upx;
		line-height: 22upx;
	}
	.icon-nv{
		background: #ff698d!important;
	}
</style>
