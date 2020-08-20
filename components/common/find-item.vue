<template>
	<view class="item-group">
		<view class="item-title">
			<view class="item-title-left">
				<image src="../../static/icons/sign_circle.png"></image>
				<text>{{about.name}}</text>
			</view>
			<view :class="{'item-title-right': about.status }">{{about.status}}</view>
		</view>
		<view class="item-detail">{{about.people + '人已加入·' + about.content + '篇内容'}}</view>
		<view class="item-img">
			<image :src="about.img1"></image>
			<image :src="about.img2"></image>
			<image :src="about.img3"></image>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			about: Object
		}
	}
</script>

<style lang="scss">
.item{
	&-group {
		box-sizing: border-box;
		padding: 20rpx 32rpx;
		border: 1px solid #F7F7F7;
		margin-bottom: 20rpx;
		border-radius: 20rpx;
		height: 350rpx;
		width: 100%;
	},
	&-title{
		display:flex;
		justify-content: space-between;
		height:32rpx;
		width:100%;
		&-left{
			display:flex;
			image{
				margin-right: 10rpx;
				width: 32rpx;
				height: 32rpx;
			}
			text{
				width: 200rpx;
				height: 32rpx;
				line-height: 32rpx;
				font-size: 20rpx;
				font-weight: bold;
			}
		}
	},
	&-detail {
		font-size: 18rpx;
		color: #ccc;
		margin: 10rpx 0;
	},
	&-img {
		display: flex;
		justify-content: space-between;
		image{
			width: 195rpx;
			height: 195rpx;
			border-radius: 20rpx;
		}
	}
}
.item-title-right{
	font-size: 16rpx;
	font-weight: bold;
	height: 32rpx;
	line-height: 32rpx;
	border-radius: 8rpx;
	width: 130rpx;
	text-align: center;
	background-color: #FFCA33;
}
</style>
