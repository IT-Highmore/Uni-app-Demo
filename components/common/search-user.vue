<template>
	<view class="content">
		<view class="content-left">
			<image style="width: 92rpx;height: 92rpx;margin-right: 20rpx;" :src="content.img"></image>
			<view class="content-detail">
				<view style="font-weight: bold;">{{content.name}}</view>
				<view style="color: #ccc;font-size: 24rpx;">{{content.focus_count + '关注'}}</view>
			</view>
		</view>
		<uni-icons class="content-right" :size="28" type="person"></uni-icons>
	</view>
</template>

<script>
	export default {
		props:{
			content: Object
		}
	}
</script>

<style>
.content {
	display: flex;
	justify-content: space-between;
	width: 686rpx;
	height: 100rpx;
	margin: 30rpx 32rpx;
}
.content-left{
	display: flex;
}
.content-detail {
	display: flex;
	flex-direction: column;
}
.content-right{
	
}
</style>
