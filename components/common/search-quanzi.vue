<template>
	<view class="content">
		<image style="width: 100rpx;height: 100rpx;margin-right: 20rpx;" :src="content.img"></image>
		<view class="content-right">
			<view class="content-right-head">
				<image style="margin-right: 10rpx;width: 32rpx;height: 32rpx;" src="../../static/icons/sign_circle.png"></image>
				<view style="font-weight: bold;">{{content.name}}</view>
			</view>
			<view class="content-right-bottom">
				<view style="color: #ccc;font-size: 24rpx;margin-right: 30rpx;">{{ content.person_count+'人已加入'}}</view>
				<view style="color: #ccc;font-size: 24rpx;">{{ content.content_count+'篇内容'}}</view>
			</view>
		</view>
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
	width: 686rpx;
	margin: 30rpx 32rpx;
}
.content-right{
	display: flex;
	flex-direction: column;
}
.content-right-head{
	display: flex;
	height: 50rpx;
	line-height: 50rpx;
	align-items: center;
	padding-bottom: 10rpx;
}
.content-right-bottom {
	display: flex;
}
</style>
