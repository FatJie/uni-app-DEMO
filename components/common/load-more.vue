<template>
	<view class="loadmore">{{loadtext}}</view>
</template>

<script>
	export default{
		props:{
			loadtext:String
		}
	}
</script>

<style scoped>
	.loadmore{
		text-align: center;
		color: #aaa;
		padding: 10upx;
	}
</style>
