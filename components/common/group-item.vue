<template>
	<view class="group-item">
		<image class="item-img" :src="item.head_img"></image>
		<view class="item-title">
			<view class="item-class">
				<image src="../../static/icons/sign_circle.png"></image>
				<text>{{item.name}}</text>
			</view>
			<view v-if="job === 2" class="item-job">管理员</view>
			<view v-else class="item-job" >圈主</view>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			item: Object,
			job: Number
		},
		data(){
			return{
				
			}
		}
	}
</script>

<style lang="scss">
.group-item {
	display: flex;
	flex-direction: column;
	justify-content: center;
	height: 350rpx;
	margin: 30rpx 32rpx;
	border-radius: 20rpx;
	box-shadow: 0 10rpx 10rpx #eceaea;
	background-color: #fff;
	box-sizing: content-box;
}
.item {
	&-img {
		width: 100%;
		height: 280rpx;
		border-radius: 20rpx 20rpx 0 0;
	},
	&-title {
		display: flex;
		align-items: center;
		justify-content: space-between;
		height: 70rpx;
	},
	&-class {
		display: flex;
		align-items: center;
		height: 70rpx;
		image {
			margin-left: 10rpx;
			margin-right: 10rpx;
			width: 32rpx;
			height: 32rpx;
		}
		text {
			line-height: 70rpx;
			font-size: 24rpx;
		}
	},
	&-job {
		width: 70rpx;
		height: 30rpx;
		font-size: 20rpx;
		line-height: 30rpx;
		margin-right: 10rpx;
		text-align: center;
		border-radius: 6rpx;
		color: #FFFFFF;
		background-color: #000000;
	}
}

</style>
